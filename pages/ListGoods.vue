<template>
  <div class="container-fluid mt--7">
    <div class="row">
      <div class="col">
        <div class="card shadow"> 
          <div class="card-header border-0">
            <div class="row align-items-center">
              <div class="col"><h3 class="mb-0"> Light Table </h3></div>
              <div class="col text-right">
                <button type="button" id="modal" data-modalid='ModalGoods' data-modaltype='insert' class="btn btn-outline-primary btn-sm" v-on:click="callModal($event)"><nuxt-link to="/NewGoods">{{ lang.Common.New + lang.Goods.Goods }}</nuxt-link></button>
              </div>
            </div>
          </div>
          <table>
            <thead>
                <tr>
                  <th>Barcode</th>
                  <th>{{ lang.Common.Name + lang.Goods.Goods }}</th>
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
          <!-- <div class="card-footer d-flex justify-content-end">
              <ul class="pagination"> 
               :class="[size && pagination-${size}`, align && `justify-content-${align}`]" 
              <li class="page-item prev-page">
                <a class="page-link" aria-label="Previous" @click="prevPage">
                  <span aria-hidden="true"><i class="fa fa-angle-left" aria-hidden="true"></i></span>
                </a>
              </li>
              <li class="page-item" :class="{active: value === item}" :key="item" v-for="item in 20">
                <a class="page-link" @click="changePage(item)">{{item}}</a>
              </li>
              <li class="page-item next-page" :class="{disabled: value === totalPages}">
                <a class="page-link" aria-label="Next" @click="nextPage">
                  <span aria-hidden="true"><i class="fa fa-angle-right" aria-hidden="true"></i></span>
                </a>
              </li> 
            </ul>
          </div> -->
        </div>
      </div>
    </div>
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
      lang () {
        return this.$t('Main')
      }
    },
    mounted() {
      console.log(this.lang);
    },
    data() {
      return {
        tabid: 1,
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
        ],
        tabs: [
          {
            id: 1,
            title: 'ข้อมูลทั่วไป'
          },
          {
            id: 2,
            title: 'หน่วยนับ'
          }
        ],
        ListUnit:[]
      }
    },
    methods: {
      switchTab: function ($val) {
        this.tabid = $val;
      },
      callModal: function (event) {
        var id = event.target.id;
        var element = document.querySelector('#' + id);
        this.dialogGoods = true;
      },
      addUnit: function () {
        var obj = {
          Barcode: '123456'
        }
        this.ListUnit.push(obj);
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

  .pointer {
    cursor: pointer;
  }
  
  .tabs {
    margin-bottom: 1.5rem;
  }

  .tabs ul{
    display: flex;
    align-items: center;
    margin: 0;
    padding: 0;
  }

  .tabs ul li {
    list-style: none;
    flex: 1 0 auto;
    max-width: none;
  }

  .tabs li {
    border-bottom: 1px solid #dbdbdb;
  }

  .tabs li.active {
    border-bottom: solid 1px #007bff;
    color: #007bff;
    /* border-bottom: solid 1px #00d1b2;
    color: #00d1b2; */
  }

  .tabs-content {
    margin-top: 10px;
  }

  .tabs-info {
    display: none;
  }

  .activeTab {
    display: block;
  }

  .modal-body {
    min-height: 40vh;
  }

  /* transaction table */
  .transaction-table th{
    text-align: left;
  }
  
  .transaction-table input[type="text"] {
    width: 100%;
    padding: 2px 10px 3px 5px;
    height: 30px;
  }

  .transaction-table .input-group input[type="text"] {
    width: 80%;
  }

  .transac-btn-picker {
    background-color: #ffffff !important;
    border: 1px solid #cccccc !important;
    border-left: none !important;
    border-radius: 0px;
    box-shadow: none;
    width: 30px;
    height: 30px;
  }

/* .transaction-table .input-group {
  border: 1px gray solid;
  padding: 6px;
}

.transaction-table .input-group input {
  border:none;
  background-color: transparent;
  height: 15px;
}

.transaction-table input {
  border: 1px gray solid;
  padding: 6px;
  height: 15px;
}

.transaction-table input.form-control:focus {
  border-color: #f2f2f2 !important;
  box-shadow: none;
} */
</style>