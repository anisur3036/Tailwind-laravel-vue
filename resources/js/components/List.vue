<template>
	<transition 
		name="expand"
		@enter="enter"
		@after-enter="afterEnter"
		@leave="leave">
		<ul v-show="list.open" class="list-item">
			<li class="sub-items pt-2 pb-2 pl-6 pr-1 border-t border-gray-600 bg-gray-800 text-gray-100 hover:text-gray-700 hover:bg-teal-500"
				v-for="(item, index) in list.sublist" :key="index">
					{{ item}}
				</li>
		</ul>
	</transition>
</template>

<script>
export default {
	props: [
		'list'
		],
		methods: {
			enter(el) {
				el.style.height = 'auto';
				const height = getComputedStyle(el).height;
				el.style.height = 0;
				getComputedStyle(el)

				setTimeout(() => {
					el.style.height = height;
				});
			},
			afterEnter(el) {
				el.style.height = 'auto';
			},
			leave(el) {
				el.style.height = getComputedStyle(el).height;
				getComputedStyle(el);

				setTimeout(() => {
					el.style.height = 0;
				});
			}
		}
}
</script>	

<style lang="scss">
	.list-item {
		.sub-items {
			// padding: 8px 0px 8px 22px;
			// text-index: 25px;
			// color: #fefefe;
			// background-color: #333;
			// border-top: 1px solid #222;

			&:hover {
				// color: #333;
				// background-color: #38B087;
			}
		}
	}
	
	.expand-enter-active, .expand-leave-active {
		transition: height .5s ease-in-out;
		overflow: hidden;
	}
</style>
