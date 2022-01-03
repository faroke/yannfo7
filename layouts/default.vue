<template>
  <div class="bg-gray-50">
    <Header />
    <Nuxt />
    <Footer />
    
  </div>
</template> 
<script>
import Footer from '@/components/Footer';
export default {
    components: {
        Footer
    }
}
</script>