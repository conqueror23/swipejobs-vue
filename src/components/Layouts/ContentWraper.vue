<template>
    <div>
       <HeadLine/>
        <Content/>
    </div>
</template>

<script>
import HeadLine from '@/components/WraperComponents/HeadLine'
import Content from '@/components/Layouts/Content'
export default {
name:"ContentWrapper",
components:{
    Content,
    HeadLine
}

}
</script>

<style>

</style>
