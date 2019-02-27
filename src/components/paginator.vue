<template>
	<div class="container">
		<table class="table table-hover">
			<thead>
				<tr>
					<th>First name</th>
					<th>Last Name</th>
					<th>Avtar</th>
				</tr>
			</thead>
			<tbody>
				<tr v-for="f in data">
					<td>{{f.first_name}}</td>
					<td>{{f.last_name}}</td>
					<td><img :src="f.avatar"></td>
				</tr>
			</tbody>
		</table>
   <paginate
    :page-count="4"
    :page-range="4"
    :margin-pages="2"
    :click-handler="clickCallback"
    :prev-text="'<'"
    :next-text="'>'"
    :container-class="'pagination'"
    :page-class="'page-item'">
  </paginate>
  <select @change="changePerPage()" id="select" class="box">
  	<option value="1">1</option>
  	<option value="2">2</option>
  	<option value="3">3</option>
  </select>
	</div>
</template>

<script>
import axios from 'axios'
	export default{
		data(){
			return{
				data: null,
				perPage: 3,
				pageNo: null
			}
		},
		created(){
            axios.get('https://reqres.in/api/users?page=1&per_page='+this.perPage)
        .then((response)=>{this.data = response.data.data})
    	},
		methods: {
    	clickCallback: function(pageNum) {

        axios.get('https://reqres.in/api/users?page='+this.pageNo+'&per_page='+this.perPage)
        .then((response)=>{this.data = response.data.data})
      	console.log(this.pageNo)
      	this.pageNo = pageNum
    	},
    	changePerPage(){
    		this.perPage = document.getElementById('select').value
    		console.log(this.perPage)
    		this.clickCallback(this.pageNum)
    	}

  	}
	}
</script>
<style>
.pagination li {
	padding: 5px;
}
.active a {
	color: red;
}
.box{
	width: 5%;
	padding: 10px 10px 10px 10px;
}
</style>

