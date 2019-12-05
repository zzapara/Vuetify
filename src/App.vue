<template>
  <v-app>
		<v-app-bar app color="primary" dark>
			<v-toolbar-title>Vuetify Dashboard</v-toolbar-title>
			<v-spacer></v-spacer>
			<v-btn 
				v-for="link in links"
				:key="`${link.lable}-footer-link`"
				text 
				rounded 
				:to="link.url"
			>
				{{link.lable}}
			</v-btn>
		</v-app-bar>
		<v-content>
			<router-view/> 
		</v-content>
		<v-footer color="primary lighten-1" padless>
			<v-layout justify-center wrap>
				<v-btn
					v-for="link in links"
					:key="`${link.lable}-footer-link`"
					color="white"
					text
					rounded
					class="my-2"
					:to="link.url"
				>
					{{ link.lable }}
				</v-btn>
				<v-flex primary lighten-2 py-4 text-center white--text xs12>
					{{ new Date().getFullYear() }} — <strong>Vuetify Dashboard</strong>
				</v-flex>
			</v-layout>
		</v-footer>
	</v-app>
</template>

<script>
export default {
	name: 'App',
	data() {
		return {
			links: [
			{
				lable:'Home',
				url: '/'	
			},
			{
				lable:'Login',
				url:'/login'
			},
			{
				lable:'Dashboard',
				url:'/dashboard'
			},
			{
				lable:'Signup',
				url:'/signup'
			}
			]
		}
	}
}
</script>
<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
