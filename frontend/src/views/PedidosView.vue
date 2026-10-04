<template>
  <section>
    <h2>Pedidos</h2>

    <AlertMessage :message="error" />

    <form class="card form-grid" @submit.prevent="guardar">
      <label class="field">
        <span>Cliente</span>
        <select v-model.number="form.cliente_id" required>
          <option disabled value="">Seleccione un cliente</option>

          <option
            v-for="cliente in clientes"
            :key="cliente.id"
            :value="cliente.id"
          >
            {{ cliente.nombre }}
          </option>
        </select>
      </label>

      <label class="field">
        <span>Producto</span>
        <select v-model.number="form.producto_id" required>
          <option disabled value="">Seleccione un producto</option>

          <option
            v-for="producto in productos"
            :key="producto.id"
            :value="producto.id"
          >
            {{ producto.nombre }} — Q{{ producto.precio }}
          </option>
        </select>
      </label>

      <BaseInput
        v-model.number="form.cantidad"
        label="Cantidad"
        type="number"
      />

      <div class="form-actions">
        <BaseButton type="submit" :disabled="guardando">
          {{ editando ? 'Actualizar' : 'Crear' }}
        </BaseButton>

        <BaseButton
          v-if="editando"
          variant="secondary"
          @click="cancelar"
        >
          Cancelar
        </BaseButton>
      </div>
    </form>

    <DataTable :rows="pedidos" :columns="columns">
      <template #actions="{ row }">
        <select
          :value="row.estado"
          @change="cambiarEstado(row, $event.target.value)"
        >
          <option value="pendiente">Pendiente</option>
          <option value="pagado">Pagado</option>
          <option value="enviado">Enviado</option>
          <option value="cancelado">Cancelado</option>
        </select>

        <BaseButton
          variant="danger"
          @click="eliminar(row)"
        >
          Eliminar
        </BaseButton>
      </template>
    </DataTable>
  </section>
</template>

<script setup>
import { onMounted, reactive, ref } from 'vue'
import { clientesApi } from '../api/clientes'
import { productosApi } from '../api/productos'
import { pedidosApi } from '../api/pedidos'
import AlertMessage from '../components/AlertMessage.vue'
import BaseButton from '../components/BaseButton.vue'
import BaseInput from '../components/BaseInput.vue'
import DataTable from '../components/DataTable.vue'

const pedidos = ref([])
const clientes = ref([])
const productos = ref([])

const error = ref('')
const guardando = ref(false)
const editando = ref(false)
const idEditando = ref(null)

const columns = [
  { key: 'id', label: 'ID' },
  { key: 'cliente', label: 'Cliente' },
  { key: 'producto', label: 'Producto' },
  { key: 'cantidad', label: 'Cantidad' },
  { key: 'estado', label: 'Estado' },
  { key: 'total', label: 'Total' },
]

const form = reactive({
  cliente_id: '',
  producto_id: '',
  cantidad: 1,
})

function limpiar() {
  Object.assign(form, {
    cliente_id: '',
    producto_id: '',
    cantidad: 1,
  })

  editando.value = false
  idEditando.value = null
}

async function cargar() {
  error.value = ''

  try {
    const [pedidosResponse, clientesResponse, productosResponse] =
      await Promise.all([
        pedidosApi.listar(),
        clientesApi.listar(),
        productosApi.listar(),
      ])

    pedidos.value = pedidosResponse.data
    clientes.value = clientesResponse.data
    productos.value = productosResponse.data
  } catch (err) {
    error.value = err.message
  }
}

async function guardar() {
  error.value = ''
  guardando.value = true

  try {
    if (editando.value) {
      await pedidosApi.actualizar(idEditando.value, {
        estado: form.estado,
      })
    } else {
      await pedidosApi.crear({
        cliente_id: form.cliente_id,
        producto_id: form.producto_id,
        cantidad: form.cantidad,
      })
    }

    limpiar()
    await cargar()
  } catch (err) {
    error.value = err.message
  } finally {
    guardando.value = false
  }
}

function editar(pedido) {
  Object.assign(form, {
    cliente_id: pedido.cliente_id,
    producto_id: pedido.producto_id,
    cantidad: pedido.cantidad,
    estado: pedido.estado,
  })

  editando.value = true
  idEditando.value = pedido.id
}

function cancelar() {
  limpiar()
}

async function cambiarEstado(pedido, estado) {
  error.value = ''

  try {
    await pedidosApi.actualizar(pedido.id, {
      estado: estado,
    })

    await cargar()
  } catch (err) {
    error.value = err.message
  }
}

async function eliminar(pedido) {
  if (!window.confirm(`¿Eliminar el pedido #${pedido.id}?`)) return

  try {
    await pedidosApi.eliminar(pedido.id)
    await cargar()
  } catch (err) {
    error.value = err.message
  }
}

onMounted(cargar)
</script>