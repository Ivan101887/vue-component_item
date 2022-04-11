<template>
	<div class="productItem">
		<div class="productItem__wrap">
			<figure class="productItem__imgWrap">
				<img
					:src="parentData.src"
					:alt="parentData.brand"
					class="productItem__img"
				/>
			</figure>
			<div class="productItem__intro">
				<em class="productItem__brand">{{ parentData.brand }}</em>
				<h2 class="productItem__feature">{{ parentData.feature }}</h2>
				<p
					:class="[
						'productItem__desc',
						{ 'productItem__desc--sm': parentData.desc.length < 24 },
					]"
				>
					{{ parentData.desc }}
				</p>
			</div>
		</div>
	</div>
</template>
<script>
	export default {
		name: "ProductItem",
		props: {
			parentData: Object,
		},
	};
</script>
<style lang="scss" scoped>
	.productItem {
		box-sizing: border-box;
		float: left;
		padding: .9375rem;
		&-lg {
			width: 50%;
		}
		&-sm {
			width: 25%;
		}
		&__wrap {
			position: relative;
			overflow: hidden;
			&:hover {
				.productItem {
					&__intro {
						bottom: .75rem;
					}
					&__brand {
						color: #ffa500;
					}
					&__img {
						transform: scale(1.2);
					}
				}
			}
		}
		&__imgWrap {
			&::before {
				content: "";
        z-index: 1;
				position: absolute;
				width: 100%;
				height: 100%;
				background: {
					image: linear-gradient(to bottom, transparent 0% 70%, rgba(0, 0, 0, 0.8));
				}
				transition: all ease-in 0.8s;
			}
		}
		&__img {
			width: 100%;
			height: auto;
			display: block;
			transition: all ease-in-out 0.8s;
		}
		&__intro {
			position: absolute;
      left: 15px;
      z-index: 2;
			bottom: -2.625rem;
			width: 100%;
			box-sizing: border-box;
			transition: all ease-in 0.8s;
		}
		&__brand {
			font: {
				size: 1.5rem;
				style: italic;
				weight: 600;
			}
			color: #ddd;
			transition: color ease-in-out 0.8s;
		}
		&__feature {
			color: #fff;
			margin: {
				top: .625rem;
				bottom: .625rem;
			}
			font: {
				size: 18px;
			}
		}
		&__desc {
			font: {
				size: .9375rem;
			}
			color: #fff;
			overflow: hidden;
			display: -webkit-box;
			white: {
				space: normal;
			}
      padding: {
        right: 25px;
      }
			line: {
				height: 1.5em;
			}
			-webkit: {
				box-orient: vertical;
				line-clamp: 2;
			}
			&--sm {
				height: 3em;
			}
		}
	}
</style>