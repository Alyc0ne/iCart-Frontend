<template>
  <div class="container-fluid mt--7">
    <div class="row">
      <div class="col">
        <div class="card shadow"> 
          <div class="card-header border-0">
            <div class="row align-items-center">
              <div class="col"><h3 class="mb-0"> Light Table </h3></div>
              <div class="col text-right">
                <button type="button" class="btn btn-primary btn-sm">See all</button>
              </div>
            </div>
          </div>
          <table>
            <thead>
                <tr>
                  <th>Barcode</th>
                  <th>Name</th>
                  <th>Qty</th>
                  <th>Cost</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="item in tableData" :key="item.GoodsID">
                  <th>{{ item.GoodsBarcode }}</th>
                  <td>{{ item.GoodsName }}</td>
                  <td>{{ item.GoodsQty }}</td>
                  <td>฿{{ item.GoodsCost }}</td>
                </tr>
              </tbody>
          </table>
          <div class="card-footer d-flex justify-content-end">
              <ul class="pagination"> 
              <!-- :class="[size && pagination-${size}`, align && `justify-content-${align}`]" -->
              <li class="page-item prev-page">
                <a class="page-link" aria-label="Previous" @click="prevPage">
                  <span aria-hidden="true"><i class="fa fa-angle-left" aria-hidden="true"></i></span>
                </a>
              </li>
              <li class="page-item" :class="{active: value === item}" :key="item" v-for="item in 20">
                <a class="page-link" @click="changePage(item)">{{item}}</a>
              </li>
              <!-- <li class="page-item next-page" :class="{disabled: value === totalPages}">
                <a class="page-link" aria-label="Next" @click="nextPage">
                  <span aria-hidden="true"><i class="fa fa-angle-right" aria-hidden="true"></i></span>
                </a>
              </li> -->
            </ul>
          </div>
        </div>
      </div>
    </div>
    <!-- <v-card class="mx-auto shadow">
      <v-card-title>
        <v-row no-gutters class="header">
        <v-col>
          <span>รายการสินค้า</span>
        </v-col>
        <v-col class="text-right">
          <v-btn outlined color="indigo">{{ langGoods.ActionNew }}</v-btn>
        </v-col>
      </v-row>
      </v-card-title>
      <v-simple-table :dense="false" :fixed-header="true" :height="450">
        <template v-slot:default>
          <thead>
            <tr>
              <th>Barcode</th>
              <th>Name</th>
              <th>Qty</th>
              <th>Cost</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="item in tableData" :key="item.GoodsID">
              <th>{{ item.GoodsBarcode }}</th>
              <td>{{ item.GoodsName }}</td>
              <td>{{ item.GoodsQty }}</td>
              <td>฿{{ item.GoodsCost }}</td>
            </tr>
          </tbody>
        </template>
      </v-simple-table>
      <v-card class="d-flex mb-6" flat tile>
        <v-card-title class="ml-auto" outlined tile>
            <v-pagination
        v-model="page"
        :length="4"
        circle
      ></v-pagination>
        </v-card-title>
      </v-card>
    </v-card>
    <ManageGoodsModal :dialogGoods="dialogGoods"/> -->
  </div>
</template>
<script>
  import ManageGoodsModal from '@/components/Shared/Modal/GoodsModal'

  export default {
    name: 'projects-table',
    components: {
      ManageGoodsModal
    },
    computed: {
      langGoods () {
        return this.$t('listGoods')
      }
    },
    data() {
      return {
        dialogGoods: false,
        page: 1,
        tableData: [
          {
            GoodsBarcode: '45862565626',
            GoodsName: 'Argon Design System',
            GoodsQty: '20',
            GoodsCost: '50,000'
          },
          {
            GoodsBarcode: '124125124214124',
            GoodsName: 'React Material Dashboard',
            GoodsQty: '45',
            GoodsCost: '2,500'
          },
          {
            GoodsBarcode: '1845564844',
            GoodsName: 'Black Dashboard',
            GoodsQty: '14',
            GoodsCost: '8,500'
          },
          {
            GoodsBarcode: '1845564844',
            GoodsName: 'Black Dashboard',
            GoodsQty: '14',
            GoodsCost: '8,500'
          },
          {
            GoodsBarcode: '1845564844',
            GoodsName: 'Black Dashboard',
            GoodsQty: '14',
            GoodsCost: '8,500'
          },
          {
            GoodsBarcode: '1845564844',
            GoodsName: 'Black Dashboard',
            GoodsQty: '14',
            GoodsCost: '8,500'
          }
        ]
      }
    }
  }
</script>
<style scoped>
  .shadow {
    box-shadow: 0 0 2rem 0 rgba(136, 152, 170, 0.15) !important;
    background-color: #fff;
    background-clip: border-box;
    border: 1px solid rgba(0, 0, 0, 0.05);
    border-radius: 0.375rem;
  }

  .card-header {
    margin-bottom: 0;
    background-color: #fff;
    border: 0 !important;
    border-radius: calc(0.375rem - 1px) calc(0.375rem - 1px) 0 0;
    width: 100%;
    color: #525f7f;
    font-weight: bold;
  }

  table {
    width: 100%;
    margin-bottom: 1rem;
    color: #525f7f;
    background-color: transparent;
  }

  .card table td, .card table th {
    padding-left: 1.5rem;
    padding-right: 1.5rem;
  }

  table.align-items-center td, table.align-items-center th {
    vertical-align: middle;
  }

  table thead th {
    padding-top: 0.75rem;
    padding-bottom: 0.75rem;
    font-size: 0.65rem;
    text-transform: uppercase;
    letter-spacing: 1px;
    border-bottom: 1px solid #e9ecef;
    background-color: #f6f9fc;
    color: #8898aa;
    border-color: #e9ecef;
  }

  table th, table td {
    padding: 1rem;
    vertical-align: top;
    border-top: 1px solid #e9ecef;
    font-size: 0.8125rem;
    white-space: nowrap;
  }

  .table-flush tbody tr:first-child td, .table-flush tbody tr:first-child th {
    border-top: 0;
  }

  table th {
    font-weight: 600;
  }

  /* table thead th {
    font-size: 0.65rem !important;
    text-transform: uppercase !important;
    letter-spacing: 1px !important;
    border-bottom: 1px solid #e9ecef !important;
    color: #8898aa !important;
    background-color: #f6f9fc !important;
    border-color: #e9ecef !important;
  }

  table th {
    font-weight: 600 !important;
    text-align: inherit !important;
  }

  table td, table th {
    padding-left: 1.5rem !important;
    padding-right: 1.5rem !important;
    font-size: 0.8125rem !important;
    white-space: nowrap !important;
    padding: 1rem !important;
    vertical-align: top !important;
    border-top: 1px solid #e9ecef !important;
  }

  table tbody tr:first-child th {
    font-size: 0.875rem !important;
  }

  table tbody tr:first-child td, table tbody tr:first-child th {
    border-top: 0 !important;
  }

  table tbody tr th {
    color: #525f7f;
  }

  table tbody tr td, table tbody tr th {
    border-bottom: 0 !important;
  } */
</style>