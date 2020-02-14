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
			<nav class="flex-1">
				<div class="flex justify-end pt-3 pb-3">
					<a class="px-1 mx-2 relative outline-none" href="#">
						<span class="badge badge--red absolute z-10">2</span>
						<svg class="w-6 h-6 fill-current text-white hover:text-black focus:text-black" xmlns="http://www.w3.org/2000/svg"> 
							<path d="M15 18.998a3 3 0 01-6 0H4a1 1 0 010-2h1v-6a7 7 0 014.02-6.34 3 3 0 015.96 0 7 7 0 014.02 6.34v6h1a1 1 0 110 2h-5zm-4 0a1 1 0 002 0h-2zm0-12.9a5 5 0 00-4 4.9v6h10v-6a5 5 0 00-4-4.9v-1.1a1 1 0 00-2 0v1.1z" />
						</svg>
					</a>
					<a class="px-1 mx-2 relative outline-none" href="#">
						<span class="badge badge--orange absolute z-10">2</span>
						<svg class="w-6 h-6 fill-current text-white hover:text-black focus:text-black" xmlns="http://www.w3.org/2000/svg">
							<path d="M4 4h16a2 2 0 012 2v12a2 2 0 01-2 2H4a2 2 0 01-2-2V6c0-1.1.9-2 2-2zm16 3.38V6H4v1.38l8 4 8-4zm0 2.24l-7.55 3.77a1 1 0 01-.9 0L4 9.62V18h16V9.62z"/>
						</svg>
					</a>
					<a class="px-1 mx-2" href="#"><img class="w-6 h-6 rounded-full border border-teal-300 outline-none" src="/img/profile-photo.png" alt="Anisur Rahman"></a>
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
	.badge {
    top: -3px;
    right: 1px;
    width: 12px;
    height: 12px;
    font-size: 8px;
    line-height: 7px;
    padding: 2px 2px 2px 4px;
    border-radius: 50%;
	}
	.badge--red {
		background-color: red;
		color: white;
	}
	.badge--orange {
		background-color: orange;
		color: white;
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
