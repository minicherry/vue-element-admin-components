/*
此组件假设数据为树形结构，以树形结构的方式进行展示
 */
<template>
  <div>
    <!-- 第一层 -->
    <div v-for="itemFirst in testItems">
      <el-checkbox
        :key="itemFirst.label"
        v-model="itemFirst.checked"
        :label="itemFirst.label"
        @change="handleCheckedChange('itemFirst',itemFirst)"
      >{{ itemFirst.label }}</el-checkbox>
      <!-- 第二层 -->
      <div
        v-for="itemSecond in itemFirst.children"
        v-if="itemFirst.children"
      >
        <el-checkbox
          :key="itemSecond.label"
          v-model="itemSecond.checked"
          :label="itemSecond.label"
          @change="handleCheckedChange('itemSecond',itemSecond)"
        >{{ itemSecond.label }}</el-checkbox>
        <!-- 第三层 -->
        <div
          v-for="itemThird in itemSecond.children"
          v-if="itemSecond.children"
        >
          <el-checkbox
            :key="itemThird.label"
            v-model="itemThird.checked"
            :label="itemThird.label"
            @change="handleCheckedChange('itemThird',itemThird)"
          >{{ itemThird.label }}</el-checkbox>
        </div>
      </div>
    </div>

  </div>
</template>
<script>
export default {
  name: 'CheckboxMore',
  data() {
    return {
      isCheckedFirst: false,
      isCheckedSecond: false,
      testItems: [
        {
          label: '一级 1',
          children: [{
            label: '二级 1-1',
            children: [{
              label: '三级 1-1-1'
            }, {
              label: '三级 1-1-2'
            }]
          }]
        },
        {
          label: '一级 2',
          children: [{
            label: '二级 2-1',
            children: [{
              label: '三级 2-1-1'
            }]
          }, {
            label: '二级 2-2',
            children: [{
              label: '三级 2-2-1'
            }]
          }]
        },
        {
          label: '一级 3',
          children: [{
            label: '二级 3-1',
            children: [{
              label: '三级 3-1-1'
            }]
          }, {
            label: '二级 3-2',
            children: [{
              label: '三级 3-2-1'
            }]
          }]
        }]
    }
  },
  created() {
    this.initData()
    // this.opreationData()
  },
  methods: {
    // 初始化数据
    initData() {
      this.testItems.forEach(item => {
        this.$set(item, 'checked', true)
        if (item.children.length > 0) {
          item.children.forEach(item => {
            this.$set(item, 'checked', true)
            if (item.children.length > 0) {
              item.children.forEach(item => {
                this.$set(item, 'checked', true)
              })
            }
          })
        }
      })
    },
    handleCheckedChange(level, item) {
      this.isCheckedFirst = item.checked
      if (level === 'itemFirst') {
        // 如果点击的是第一层
        item.checked = this.isCheckedFirst
        if (item.children.length > 0) {
          // 把第二层的item全部随第一层变化
          item.children.forEach(item => {
            item.checked = this.isCheckedFirst
            // 把第三层的item全部随第一层变化
            if (item.children.length > 0) {
              item.children.forEach(item => {
                item.checked = this.isCheckedFirst
              })
            }
          })
        }
      } else if (level === 'itemSecond') {
        // 如果点击的是第二层
        if (item.children.length > 0) {
          this.isCheckedSecond = item.checked
          // 把第三层的item全部随第一层变化
          item.children.forEach(item => {
            item.checked = this.isCheckedSecond
          })
        }
      }
      // console.log(this.testItems)
      this.opreationData()
    },
    opreationData() {
      this.testItems.forEach(item => {
        item.children.forEach(item => {
          if (item.children && item.children.length > 0) {
            item.checked = item.children.some(item => item.checked)
          }
        })

        if (item.children && item.children.length > 0) {
          item.checked = item.children.some(item => item.checked)
        }
      })
    }
    /* handleCheckAllChange(val) {
      this.checkedCities = val ? cityOptions : []
      this.isIndeterminate = false
    },
    handleCheckedCitiesChange(value) {
      const checkedCount = value.length
      this.checkAll = checkedCount === this.children.length
      this.isIndeterminate = checkedCount > 0 && checkedCount < this.children.length
    } */
  }
}
</script>

