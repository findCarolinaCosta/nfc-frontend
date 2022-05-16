<template>
  <section class="bg-[#FBFDFE] w-[288px] h-screen">
    <section class="flex justify-start items-center p-5 gap-1">
      <Logo />
      <CashforceLogo />
    </section>
    <nav
      class="flex items-center gap-3 text-sm text-[#00AD8C] border-l-4 border-[#00ad8c] border-solid"
    >
      <div class="h-[64px] w-[4px]"></div>
      <InvoiceSectionIcon color="#00AD8C" classProps="ml-4" />
      <h1 class="leading-[18.23px] font-medium">Notas fiscais</h1>
    </nav>
  </section>
</template>

<script>
import Logo from "@/components/contents/Logo.vue";
import CashforceLogo from "@/components/contents/CashforceLogo.vue";
import InvoiceSectionIcon from "@/components/contents/InvoiceSectionIcon.vue";
export default {
  name: "SideBar",
  components: {
    Logo,
    CashforceLogo,
    InvoiceSectionIcon,
  },
};
</script>
