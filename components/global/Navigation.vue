<template>
    <div class="navigation">
        <nav>
            <ul role="menu">
                <li v-for="(navItem, index) in posts" :key="index">
                    <nuxt-link :to="'/' + navItem.fields.slug.trim()" role="menuitem">{{ navItem.fields.navTitle }}</nuxt-link>
                </li>
            </ul>
        </nav>
    </div>
</template>
    
<script>
export default {
    name: 'Navigation'
}
</script>

<style scoped>

</style>