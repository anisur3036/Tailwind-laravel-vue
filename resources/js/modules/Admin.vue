<template>
	<div class="relative">
		<header class="flex items-center bg-teal-500 relative z-20">
				<a href="#" title="logo" :class="isOpen ? 'w-56' : 'w-16'" class="flex items-center pt-3 pb-3 bg-teal-600 pl-3 pr-3">
					<span><svg width="24" height="24" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M19 10h2a1 1 0 010 2h-2v2a1 1 0 01-2 0v-2h-2a1 1 0 010-2h2V8a1 1 0 012 0v2zM9 12A5 5 0 119 2a5 5 0 010 10zm0-2a3 3 0 100-6.001A3 3 0 009 10zm8 11a1 1 0 01-2 0v-2a3 3 0 00-3-3H7a3 3 0 00-3 3v2a1 1 0 11-2 0v-2a5 5 0 015-5h5a5 5 0 015 5v2z" fill="#000"/></svg></span>
					<span :class="isOpen ? 'block' : 'hidden'">Large Logo</span>
				</a>
				<a href="#" @click="isOpen = !isOpen" class="text-white p-3 hover:bg-teal-600">
					<svg class="w-6 h-6 fill-current" xmlns="http://www.w3.org/2000/svg">
						<path d="M4 5h16a1 1 0 110 2H4a1 1 0 010-2zm0 6h16a1 1 0 010 2H4a1 1 0 010-2zm0 6h16a1 1 0 010 2H4a1 1 0 010-2z"/>
					</svg>
				</a>
			<nav class="flex flex-1 justify-end">
				<div class="pt-3 pb-3">
					<a href="#">Message</a>
					<a href="#">Notification</a>
					<a href="#">Flag</a>
					<a href="#">UserSetting</a>
				</div>
			</nav>
		</header>
		<aside v-if="isOpen" class="h-screen bg-teal-500 pt-20 fixed overflow-y-auto top-0 left-0 bottom-0 w-56">
			<ul class="sidenav bg-teal-600 shadow-sm overflow-hidden rounded">
				<li class="relative text-gray-300 border-t border-teal-300 cursor-pointer hover:text-black hover:bg-teal-500" v-for="(item, index) in list" :key="'item' + index">
					<svg class="icon w-4 h-4 fill-current" :class="{'open' : item.open }" xmlns="http://www.w3.org/2000/svg">
						<path d="M9.3 8.702a1 1 0 011.4-1.4l4 4a1 1 0 010 1.4l-4 4a1 1 0 01-1.4-1.4l3.29-3.3-3.3-3.3h.01z" />
					</svg>
					<div class="title py-1 px-0" @click="item.open = !item.open">
						{{ item.title }}
					</div>
					<ListItem :list="item" />
				</li>
			</ul>
		</aside>
		<p :class="isOpen ? 'ml-56' : 'ml-0'">Lorem ipsum dolor sit amet, </p>
	</div>
</template>

<script>
import ListItem from '../components/List.vue';
export default {
	components: {
		ListItem
	},
  data() {
  	return {
      isOpen: true,
      list: [
      {
      	title: 'Projects',
      	open: false,
      	sublist: [
      		'Vuejs', 'JavaScript', 'PHP', 'Laravel'
      	]
      },
      {
      	title: 'Training',
      	open: false,
      	sublist: [
      		'Online', 'Offline', 'Source Code'
      	]
      },
      {
      	title: 'Portfolio',
      	open: false,
      	sublist: [
      		'Server less', 'Recent Project', 'Herokuapp', 'Github'
      	]
      },
      {
      	title: 'About',
      	open: false,
      	sublist: [
      		'Me', 'Degree', 'Certificate'
      	]
      }
      ]
  	}
  }
}
</script>	

<style lang="scss">
	.sidenav li:last-child{
    border-bottom: 1px solid #81e6d9;
	}
	.title {
		text-indent: 20px;
	}
	svg.icon {
		position: absolute;
		top: 5px;
		right: 10px;
		transition: transform .3s ease-in-out;

		&.open {
			right: 8px;
			transform: rotateZ(90deg);
		}
	}


	::-webkit-scrollbar {
	  width: 10px;
	}

	/* Track */
	::-webkit-scrollbar-track {
	  background: #38b2ac;
	}

	/* Handle */
	::-webkit-scrollbar-thumb {
	  background: #31979B;
	}

	/* Handle on hover */
	::-webkit-scrollbar-thumb:hover {
	  background: #555;
	}
</style>
