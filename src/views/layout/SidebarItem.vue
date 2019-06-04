<template>
	<div class='menu-wrapper'>
	
	<template v-for="item in routes">
		<!-- <router-link v-if="item.children.length>0" :to="item.code+'/'+item.children[0].code">
			<el-menu-item :index="item.code+'/'+item.children[0].code" class='submenu-title-noDropdown'>
				<icon-svg v-if='item.icon' :icon-class="item.icon"></icon-svg>
				<span slot="title">{{item.children[0].title}}</span>
			</el-menu-item>
		</router-link> -->
<!--		<el-submenu :index="item.title" :key="item.name">-->
<!--			<template slot="title">-->
<!--				<icon-svg v-if='item.icon' :icon-class="item.icon"></icon-svg>-->
<!--				<span>{{item.title}}</span>-->
<!--			</template>-->
<!--			<template v-for="child in item.children">-->
<!--            <div v-if="child.redirect != '0'" style="padding-left: 30px">-->
<!--              <router-link v-if="child.href!=null&&child.href.indexOf('http')!=0&&child.href!=''"  :to="'/'+item.code+'/'+child.code" :key="child.name">-->
<!--                <el-menu-item :index="'/'+item.code+'/'+child.code">-->
<!--                  <icon-svg v-if='child.icon' :icon-class="child.icon"></icon-svg>-->
<!--                  <span>{{child.title}}</span>-->
<!--                </el-menu-item>-->
<!--              </router-link>-->
<!--              <div v-if="child.children.children!=null && child.children.children.length>0"  style="padding-left: 20px">-->
<!--                <sidebar-item class='nest-menu' v-if='child.children&&child.children.length>0' :routes='[child]' :key="child.name"> </sidebar-item>-->
<!--              </div>-->
<!--            </div>-->
<!--            <div v-if="child.redirect != '1'">-->
<!--              <sidebar-item class='nest-menu' v-if='child.children&&child.children.length>0' :routes='[child]' :key="child.name"> </sidebar-item>-->
<!--            </div>-->

<!--&lt;!&ndash;        <div v-if="1" style="padding-left: 20px">&ndash;&gt;-->
<!--        &lt;!&ndash;        </div>&ndash;&gt;-->
<!--&lt;!&ndash;        <div v-else>&ndash;&gt;-->
<!--&lt;!&ndash;          <sidebar-item class='nest-menu' v-if='child.children&&child.children.length>0' :routes='[child]' :key="child.name"> </sidebar-item>&ndash;&gt;-->
<!--&lt;!&ndash;        </div>&ndash;&gt;-->

<!--      </template>-->
<!--		</el-submenu>-->



    <el-submenu :index="item.title" :key="item.name">
      <template slot="title">
        <!--        <icon-svg v-if='item.icon' :icon-class="item.icon"></icon-svg>-->
        <span>{{item.title}}</span>
        <!--        <i class="el-icon-location"></i>-->
        <!--        <span>导航一</span>-->
      </template>
      <template v-for="child in item.children">
        <div v-if="child.children != null && child.children.length>0">
          <el-submenu :index="child.id">
            <template slot="title">{{child.title}}</template>
            <template v-for="child1 in child.children">
              <router-link v-if="child1.href!=null&&child1.href.indexOf('http')!=0&&child1.href!=''"  :to="'/'+child.code+'/'+child1.code" :key="child.name">
                <el-menu-item :index="child1.id">{{child1.title}}</el-menu-item>
              </router-link>
            </template>
          </el-submenu>
        </div>
        <div v-else>
          <router-link v-if="child.href!=null&&child.href.indexOf('http')!=0&&child.href!=''"  :to="'/'+item.code+'/'+child.code" :key="child.name">
            <el-menu-item :index="child.id">{{child.title}}</el-menu-item>
          </router-link>
        </div>

      </template>

    </el-submenu>
	</template>

	</div>
</template>

<script>
  export default {
    name: 'SidebarItem',
    props: {
      routes: {
        type: Array
      }
    },
    data() {
      return {
        status: 0
      };
    }
  }
</script>

<style rel="stylesheet/scss" lang="scss" scoped>


</style>

