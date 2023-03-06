<template>
  <div>loading: {{ loading }}</div>
  <div class="parent">
    <div class="div1">
      数据
      <textarea v-model="data" style="height: 200px; width: 100%"></textarea>
    </div>
    <div class="div2">
      公式
      <textarea v-model="formula" style="height: 200px; width: 100%"></textarea>
    </div>
    <div class="div3">
      结果
      <div>{{ result }}</div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { onMounted, ref, watch } from 'vue';
import init, { run } from 'formula-rs-wasm';
import wasmPath from 'formula-rs-wasm/formula_rs_wasm_bg.wasm?url';

const loading = ref(true);
onMounted(() => {
  init(wasmPath).then(() => {
    loading.value = false;
  });
});

const data = ref(`{"customfield_5283444":[1665886],"issueNumber":153,"dueDate":1654682400000,"totalActualLabour":9,"sprint":13145105,"estimateLabour":10,"priorityVO":{"color":"#F07E2E","description":"可能阻碍进展的严重问题。","iconUrl":"http://10.11.0.103:23288/images/icons/priorities/high.svg","id":4,"name":"高","optionKey":"High","sequence":4},"customfield_11091353":"7767207","ownerVO":{"avatar":"https://static.ligai.cn/pms/user_head/5b26032373cd41b0829edec80b8c0a61.png","id":1675286,"name":"瀚瀛"},"labelVO":[],"id":19828736,"customfield_13355621":"","follows":[],"priority":4,"statusVO":{"id":1794711,"name":"会议中","stateCategory":3,"stateName":"会议中"},"totalEstimateLabour":10,"estimatePoint":0,"sprintVO":{"assignee":1675286,"deleteFlag":0,"endDate":1640707199000,"goal":"","id":13145105,"name":"测试迭代","projectId":1784821,"startDate":1640620800000,"started":1,"status":1},"issueTypeIdVO":{"code":"story","description":"","iconUrl":"iconissue1","id":1784872,"name":"Story","originName":"Story","selectId":1784872,"source":"custom","updateTime":1634309952572},"actualLabour":9,"customfield_18190212":"7777979.0","autoCalculateFlag":1,"followsVO":[],"projectId":1784821,"workflowId":1784843,"startDate":1654477200000,"status":1794711,"remainingLabourModified":1,"description":"12312aeada","totalRemainingLabour":7,"customfield_8422994":"-10771","issueTypeId":1784872,"updateBy":1675286,"customfield_18804540":"-1789172.0","customfield_5283444VO":[{"accountEnabled":1,"icon":"https://static.ligai.cn/pms/user_head/a7c9eb0df1fa43ba930b11616f7de735.png","name":"陈俊明","value":1665886}],"owner":1675286,"summary":"4654654","remainingLabour":7,"updateTime":1656471571893,"label":[],"updateByVO":{"id":1675286,"name":"瀚瀛"},"createBy":1675286,"createTime":1648693593920,"createByVO":{"id":1675286,"name":"瀚瀛"},"tenantId":1,"subtask":[{"remainingLabourModified":0,"issueNumber":160,"issueTypeId":5,"updateBy":1675286,"labelVO":[],"id":19995836,"summary":"56464456546","follows":[],"updateTime":1654744049095,"label":[],"updateByVO":{"id":1675286,"name":"瀚瀛"},"parentId":19828736,"createBy":1675286,"statusVO":{"id":1784828,"name":"已完成","stateCategory":4,"stateName":"已完成"},"estimatePoint":0,"createTime":1648801142844,"createByVO":{"id":1675286,"name":"瀚瀛"},"tenantId":1,"issueTypeIdVO":{"code":"subtask","description":"","iconUrl":"https://static.ligai.cn/static/images/SAAS_MODULES/subtask@2x.png","id":5,"name":"子任务","originName":"子任务","selectId":5,"source":"system","updateTime":1615815617601},"autoCalculateFlag":0,"followsVO":[],"projectId":1784821,"workflowId":1784829,"status":4},{"remainingLabourModified":0,"issueNumber":161,"issueTypeId":5,"updateBy":1675286,"labelVO":[],"id":19995843,"summary":"46463164156","follows":[],"updateTime":1654744053854,"label":[],"updateByVO":{"id":1675286,"name":"瀚瀛"},"parentId":19828736,"createBy":1675286,"statusVO":{"id":1784828,"name":"已完成","stateCategory":4,"stateName":"已完成"},"estimatePoint":0,"createTime":1648801144230,"createByVO":{"id":1675286,"name":"瀚瀛"},"tenantId":1,"issueTypeIdVO":{"code":"subtask","description":"","iconUrl":"https://static.ligai.cn/static/images/SAAS_MODULES/subtask@2x.png","id":5,"name":"子任务","originName":"子任务","selectId":5,"source":"system","updateTime":1615815617601},"autoCalculateFlag":0,"followsVO":[],"projectId":1784821,"workflowId":1784829,"status":4},{"remainingLabourModified":0,"issueNumber":163,"issueTypeId":5,"updateBy":1675286,"labelVO":[],"id":19995850,"summary":"161321231561","follows":[],"updateTime":1648801161138,"label":[],"updateByVO":{"id":1675286,"name":"瀚瀛"},"parentId":19828736,"createBy":1675286,"statusVO":{"id":1784828,"name":"已完成","stateCategory":4,"stateName":"已完成"},"createTime":1648801147492,"createByVO":{"id":1675286,"name":"瀚瀛"},"tenantId":1,"issueTypeIdVO":{"code":"subtask","description":"","iconUrl":"https://static.ligai.cn/static/images/SAAS_MODULES/subtask@2x.png","id":5,"name":"子任务","originName":"子任务","selectId":5,"source":"system","updateTime":1615815617601},"autoCalculateFlag":0,"followsVO":[],"projectId":1784821,"workflowId":1784829,"status":4},{"remainingLabourModified":0,"issueNumber":164,"issueTypeId":5,"updateBy":1675286,"labelVO":[],"id":19995857,"summary":"6156165489646461","follows":[],"updateTime":1648801149698,"label":[],"updateByVO":{"id":1675286,"name":"瀚瀛"},"parentId":19828736,"createBy":1675286,"statusVO":{"id":1784826,"name":"未开始","stateCategory":2,"stateName":"未开始"},"createTime":1648801149698,"createByVO":{"id":1675286,"name":"瀚瀛"},"tenantId":1,"issueTypeIdVO":{"code":"subtask","description":"","iconUrl":"https://static.ligai.cn/static/images/SAAS_MODULES/subtask@2x.png","id":5,"name":"子任务","originName":"子任务","selectId":5,"source":"system","updateTime":1615815617601},"autoCalculateFlag":0,"followsVO":[],"projectId":1784821,"workflowId":1784829,"status":2},{"remainingLabourModified":0,"issueNumber":165,"issueTypeId":5,"updateBy":1675286,"labelVO":[],"id":19995870,"summary":"1616545641351563","follows":[],"updateTime":1648801164799,"label":[],"updateByVO":{"id":1675286,"name":"瀚瀛"},"parentId":19828736,"createBy":1675286,"statusVO":{"id":1784828,"name":"已完成","stateCategory":4,"stateName":"已完成"},"createTime":1648801151847,"createByVO":{"id":1675286,"name":"瀚瀛"},"tenantId":1,"issueTypeIdVO":{"code":"subtask","description":"","iconUrl":"https://static.ligai.cn/static/images/SAAS_MODULES/subtask@2x.png","id":5,"name":"子任务","originName":"子任务","selectId":5,"source":"system","updateTime":1615815617601},"autoCalculateFlag":0,"followsVO":[],"projectId":1784821,"workflowId":1784829,"status":4},{"remainingLabourModified":0,"issueNumber":162,"issueTypeId":5,"updateBy":1675286,"labelVO":[],"id":19999011,"summary":"164864561","follows":[],"updateTime":1648801170859,"label":[],"updateByVO":{"id":1675286,"name":"瀚瀛"},"parentId":19828736,"createBy":1675286,"statusVO":{"id":1784828,"name":"已完成","stateCategory":4,"stateName":"已完成"},"createTime":1648801145802,"createByVO":{"id":1675286,"name":"瀚瀛"},"tenantId":1,"issueTypeIdVO":{"code":"subtask","description":"","iconUrl":"https://static.ligai.cn/static/images/SAAS_MODULES/subtask@2x.png","id":5,"name":"子任务","originName":"子任务","selectId":5,"source":"system","updateTime":1615815617601},"autoCalculateFlag":0,"followsVO":[],"projectId":1784821,"workflowId":1784829,"status":4}],"relationship":[{"linkType":"IS_CAUSED_BY","id":23316864,"destinationIssueId":2381289,"issueTypeId":null,"type":"IS_CAUSED_BY"},{"linkType":"IS_CAUSED_BY","id":23316866,"destinationIssueId":9660400,"issueTypeId":null,"type":"IS_CAUSED_BY"},{"linkType":"IS_CAUSED_BY","id":23316868,"destinationIssueId":22623429,"issueTypeId":null,"type":"IS_CAUSED_BY"},{"linkType":"IS_CAUSED_BY","id":23316870,"destinationIssueId":17134290,"issueTypeId":null,"type":"IS_CAUSED_BY"},{"linkType":"CAUSES","id":23320785,"destinationIssueId":16954227,"issueTypeId":null,"type":"CAUSES"},{"linkType":"PARENT","id":31517338,"destinationIssueId":12426076,"issueTypeId":null,"type":"PARENT"},{"linkType":"DUPLICATES","id":31517402,"destinationIssueId":31517401,"issueTypeId":null,"type":"DUPLICATES"}]}`);
const formula = ref(`COUNT(subtask;status=4)/COUNT(subtask;)`);

watch(
  [data, formula, loading],
  () => {
    if (data.value && formula.value && loading.value === false) {
      result.value = run(
        formula.value,
        data.value,
        BigInt(Date.now()),
        BigInt(Date.now() - (Date.now() % 86400000))
      );
    }
  },
  { immediate: true }
);

const result = ref('');
</script>

<style scoped>
.parent {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-template-rows: repeat(2, 1fr);
  grid-column-gap: 0px;
  grid-row-gap: 0px;
}

.parent > div {
  padding: 40px;
}

.div1 {
  grid-area: 1 / 1 / 2 / 2;
}
.div2 {
  grid-area: 1 / 2 / 2 / 3;
}
.div3 {
  grid-area: 2 / 1 / 3 / 3;
}
</style>
