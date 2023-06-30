<template>
    <div>
        <header style="text-align: center; font-size: 30px; font-weight: bold;">USER DATA</header>
        <div class="row">
            <div class="col-12 mt-4">
                <button type="button" class="btn btn-success" style="float: right; margin-left: 1rem;"
                    @click="excelDownLoad()">
                    download
                    <font-awesome-icon icon="fa-solid fa-file-arrow-down" />
                </button>
                <button type="button" class="btn btn-primary" style="float: right;" @click="callData()">
                    callData
                    <font-awesome-icon icon="fa-solid fa-database" />
                </button>
            </div>
        </div>
        <div class="row" style="height: 70%;">
            <div class="col-12" style="height: 70%;">
                <div class="table-responsive mt-4" style="height: 100%;">
                    <table id="userTable" class="table mb-0 overflow-y-auto" style="text-align: center;">
                        <thead>
                            <tr>
                                <th class="font-weight-bolder" scope="col">
                                    NAME
                                </th>
                                <th class="font-weight-bolder" scope="col">
                                    USERNAME
                                </th>
                                <th class="font-weight-bolder" scope="col">
                                    EMAIL
                                </th>
                                <th class="font-weight-bolder" scope="col">
                                    PHONE
                                </th>
                                <th class="font-weight-bolder" scope="col">
                                    WEB SITE
                                </th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr v-for="user in userData" :key="user.id">
                                <td>
                                    {{ user.name }}
                                </td>
                                <td>
                                    {{ user.username }}
                                </td>
                                <td>
                                    {{ user.email }}
                                </td>
                                <td>
                                    {{ user.phone }}
                                </td>
                                <td>
                                    {{ user.website }}
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import * as XLSX from 'xlsx'
import axios from 'axios'

export default {
    data() {
        return {
            userData: []
        }
    },

    methods: {
        excelDownLoad() {
            const wb = XLSX.utils.book_new()
            const ws = XLSX.utils.table_to_sheet(document.querySelector('#userTable'))
            XLSX.utils.book_append_sheet(wb, ws, 'user-data')
            XLSX.writeFile(wb, 'user-data.xlsx')
        },

        callData() {
            axios.get('https://jsonplaceholder.typicode.com/users')
                .then(res => {
                    this.userData = res.data
                    console.log(this.userData)
                })
                .catch(err => {
                    console.log(err)
                })
        }
    }
}
</script>

<style></style>