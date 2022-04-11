<template>
	<main class="container mx-auto">
		<section class="product fix-float">
			<ProductItem
				v-for="(item, index) in data"
				:key="index"
				:class="['productItem', index === 0 ? 'productItem-lg' : 'productItem-sm']"
				:parentData="item"
			/>
		</section>
	</main>
</template>
<script>
	import ProductItem from "./ProductItem.vue";
	export default {
		components: { ProductItem },
		name: "Product",
		data() {
			return {
				data: [],
			};
		},
		async created() {
			try {
				const api = "./data.json";
				const res = await this.$http.get(api);
				this.data = res.data;
			} catch (e) {
				console.log("資料連結失敗:\n", e);
			}
		},
	};
</script>
<style lang="scss" scoped>
.product {
  overflow: hidden;
  padding: 15px;
}
</style>