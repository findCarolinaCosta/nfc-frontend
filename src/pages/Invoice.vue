<template>
  <main class="col-start-2 col-end-5 mt-[64px]">
    <div class="border-solid border-[1px] border-[#dfe2eb]"></div>
    <div class="ml-[48px] mt-[47px]">
      <section class="flex gap-2 items-center">
        <InvoiceSectionIcon color="#021B51" />
        <h1 class="text-[#021B51] text-[24px] leading-7 font-bold">
          Notas fiscais
        </h1>
      </section>
      <p class="text-sm text-[#727D94] font-normal">
        Visualize as notas fiscais que você tem.
      </p>
      <table
        class="text-center mr-[47px] text-sm text-[#4D5566] w-[1177px]"
        v-if="invoiceData.length > 0"
      >
        <tr
          class="grid grid-flow-col grid-cols-8 text-[#A1A8B8] text-base mt-[19px] mb-[19px]"
        >
          <th v-for="header in headers" :key="header">
            {{ header }}
          </th>
        </tr>
        <tr
          v-for="invoice in invoiceData"
          :key="invoice.id"
          class="grid grid-flow-col grid-cols-8 border-[#dfe2eb] border-solid border-[1px] mb-[16px] items-center font-medium text-sm gap-[15px]"
        >
          <td>{{ invoice.nNf }}</td>
          <td>{{ invoice.buyer.name }}</td>
          <td>{{ invoice.provider.name }}</td>
          <td>{{ invoice.emissionDate }}</td>
          <td class="text-[#00AD8C]">R$ {{ invoice.value }}</td>
          <td class="text-[#00AD8C] font-bold">
            {{ status[invoice.orderStatusBuyer] }}
          </td>
          <td class="text-[#727D94] text-xs col-start-7 col-end-8 ml-[95px]">
            <button
              type="button"
              class="border-[1px] pt-[8px] pr-[29px] pb-[8px] pl-[29px] rounded-[24px] border-[#CAD3FF] m-[8px] w-[165px] h-[32px]"
            >
              Dados do cedente
            </button>
          </td>
        </tr>
      </table>
      <p v-else class="text-lg font-bold text-[#4D5566] mt-[30px] ml-8">
        Loading...
      </p>
    </div>
  </main>
</template>

<script>
import Vue from "vue";
import { api } from "@/services/api";
import InvoiceSectionIcon from "@/components/contents/InvoiceSectionIcon.vue";

export default Vue.extend({
  name: "Invoice",
  components: {
    InvoiceSectionIcon,
  },
  mounted() {
    api.get("/account/nfc").then((response) => {
      this.invoiceData = response.data;
    });
  },
  data() {
    return {
      headers: [
        "NOTA FISCAL",
        "SACADO",
        "CEDENTE",
        "EMISSÃO",
        "VALOR",
        "STATUS",
      ],
      invoiceData: [],
      status: [
        "Pendente de confirmação",
        "Pedido confirmado",
        "Não reconhece o pedido",
        "Mercadoria não recebida",
        "Recebida com avaria",
        "Devolvida",
        "Recebida com devolução parcial",
        "Recebida e confirmada",
        "Pagamento Autorizado",
      ],
    };
  },
});
</script>
