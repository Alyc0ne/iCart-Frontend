<template>
  <div class="container-fluid mt--7">
    <div class="row">
      <div class="col">
        <div class="card shadow"> 
          <div class="card-header border-0">
            <div class="row align-items-center">
              <div class="col"><h3 class="mb-0"> </h3></div>
              <div class="col text-right"></div>
            </div>
          </div>
          <div class="body-content">
            <div class="tabs">
              <ul>
                <li v-for="tab in tabs" :key="tab.id" :class="{ active : tab.id == tabid }" :disabled="{ disabled : tab.id == 3 }">
                    <a class="pointer" @click="switchTab(tab.id)">{{ tab.title }}</a>
                </li>
              </ul>
            </div>

            <form>
              <div class="tabs-content">
                <div class="tabs-info" :class="{activeTab : tabid == 1}">
                  <div class="col-sm-12">
                    <div class="subtopic">ข้อมูลสินค้า</div>
                  </div>
                    <div class="clean"></div>
                    <div class="form-group row">
                      <label for="GoodsName" class="col-sm-2 col-form-label text-left">
                        <span class="req">*</span>{{ lang.Common.No + lang.Goods.Goods }}
                      </label>
                      <div class="col-sm-10">
                        <input type="text" class="form-control w40vw" id="GoodsNo" disabled>
                      </div>
                    </div>
                    <div class="form-group row">
                      <label for="GoodsName" class="col-sm-2 col-form-label text-left">
                        <span class="req">*</span>{{ lang.Common.Name + lang.Goods.Goods }}
                      </label>
                      <div class="col-sm-10">
                        <input type="text" class="form-control w40vw" id="GoodsName">
                      </div>
                    </div>
                    <div class="form-group row">
                      <label for="CateNo" class="col-sm-2 col-form-label text-left">
                        <span class="req">*</span>หมวดหมู่{{ lang.Goods.Goods }}
                      </label>
                      <div class="col-sm-10 group-picker">
                        <input type="text" class="form-control w15vw" id="CateNo" disabled>
                        <input type="text" class="form-control w20vw" id="CateName" disabled>
                      </div>
                    </div>
                    <div class="form-group row">
                      <label for="GoodsDesc" class="col-sm-2 col-form-label text-left">
                        <span class="req"></span>{{ lang.Common.Detail }}
                      </label>
                      <div class="col-sm-10">
                      <textarea class="form-control w40vw" id="GoodsDesc" rows="3"></textarea>
                      </div>
                    </div>
                    <div class="subtopic">
                        รายละเอียดราคา
                    </div>
                    <div class="clean"></div>
                    <div class="form-group row">
                        <label for="GoodsCost" class="col-sm-2 col-form-label text-left">
                          <span class="req"></span>ราคาต้นทุน
                        </label>
                        <div class="col-sm-10">
                            <input type="text" class="form-control w40vw text-right" id="GoodsCost" placeholder="0.00">
                        </div>
                    </div>
                    <div class="form-group row">
                        <label for="GoodsPrice" class="col-sm-2 col-form-label text-left">
                          <span class="req">*</span>ราคาขาย
                        </label>
                        <div class="col-sm-10">
                            <input type="text" class="form-control w40vw text-right" id="GoodsPrice" placeholder="0.00">
                        </div>
                    </div>
                </div>

                <!-- Tab Unit -->
                <div class="tabs-info" :class="{activeTab : tabid == 2}">
                  <div class="card shadow"> 
                    <div class="card-header border-0">
                      <div class="row align-items-center">
                        <div class="col text-right">
                          <button type="button" id="modal" data-modalid='ModalGoods' data-modaltype='insert' class="btn btn-outline-primary btn-sm" v-on:click="addUnit($event)">เพิ่มหน่วยนับ <font-awesome-icon :icon="['fas', 'envelope']" /> </button>
                        </div>
                      </div>
                    </div>
                    <table class="transaction-table">
                      <thead>
                          <tr>
                            <th></th>
                            <th>Barcode</th>
                            <th>{{ lang.Common.No + lang.Unit.Unit }}</th>
                            <th>{{ lang.Common.Name + lang.Unit.Unit }}</th>
                            <th>{{ lang.Unit.BaseUnit }}</th>
                            <th>อัตราส่วน</th>
                            <th></th>
                          </tr>
                        </thead>
                        <tbody v-if="!!ListUnit">
                          <tr v-for="item in ListUnit" :key="item.uid">
                            <td>
                              <font-awesome-icon :icon="['fas', 'check']" />
                              <font-awesome-icon :icon="['fas', 'times']" />
                            </td>
                            <td><input type="text" class="form-control"></td>
                            <td>
                              <div class="form-row">
                                <div class="input-group">
                                  <input type="text" class="form-control" disabled>
                                  <span class="input-group-btn">
                                    <!-- <button class="transac-btn-picker" type="button"><font-awesome-icon :icon="['fas', 'search']" @click="this.dialogUnit = true"/></button> -->
                                    <button class="transac-btn-picker" type="button"><font-awesome-icon :icon="['fas', 'search']" @click="callModal(true)"/></button>
                                  </span>
                                </div>
                              </div>
                            </td>
                            <td><input type="text" class="form-control" disabled></td>
                            <td>
                              <div class="custom-control custom-checkbox">
                                <input type="checkbox" class="custom-control-input" id="IsBaseUnit">
                                <label class="custom-control-label" for="IsBaseUnit"></label>
                              </div>
                            </td>
                            <td><input type="text" class="form-control"></td>
                          </tr>
                        </tbody>
                        <tbody v-else>
                          <tr>
                            <td colspan="4">กรุณาเพิ่มหน่วยนับ</td>
                          </tr>
                        </tbody>
                    </table>
                  </div>
                  <div class="modal-backdrop">
                    <ManageUnitModal v-bind:dialog="dialogUnit"/>
                  </div>
                  
                </div>

                <div class="tabs-info" :class="{activeTab : tabid == 3}">

                </div>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
  import ManageUnitModal from '@/components/Shared/Modal/ManageUnitModal'

  export default {
    name: 'NewGoods',
    components: {
      ManageUnitModal
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
          tabs: [
          {
            id: 1,
            title: 'ข้อมูลทั่วไป'
          },
          {
            id: 2,
            title: 'หน่วยนับ'
          },
          {
            id: 3,
            title: 'รูปภาพ'
          }
        ],
        ListUnit:[],
        dialogUnit: false
      }
    },
    methods: {
      switchTab: function ($val) {
        this.tabid = $val;
      },
      callModal: function (event) {
        // var id = event.target.id;
        // var element = document.querySelector('#' + id);
        this.dialogUnit = true;
        console.log('callmodal')
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
    text-align: left;
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
  }

  .tabs li a {
   padding-left: 10px;
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
</style>