<template>
	<main>
		<section class="product"></section>
		<ProductItem />
	</main>
</template>
<script>
import ProductItem from './ProductItem.vue';
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
        console.log(this.data);
			} catch (e) {
        console.log('資料連結失敗:\n',e);
      }
		},
	};
</script>