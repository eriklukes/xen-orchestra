<template>
  <ModalContainer tag="form">
    <template #header>
      <div :class="borderClass" class="title-bar">
        <UiIcon :class="textClass" :icon />
        <slot name="title" />
        <ModalCloseIcon class="close-icon" />
      </div>
    </template>

    <template #default>
      <slot />
    </template>

    <template #footer>
      <UiButtonGroup class="footer-buttons">
        <slot name="buttons" />
      </UiButtonGroup>
    </template>
  </ModalContainer>
</template>

<script lang="ts" setup>
import UiIcon from '@/components/ui/icon/UiIcon.vue'
import ModalCloseIcon from '@/components/ui/modals/ModalCloseIcon.vue'
import ModalContainer from '@/components/ui/modals/ModalContainer.vue'
import UiButtonGroup from '@/components/ui/UiButtonGroup.vue'
import { useContext } from '@/composables/context.composable'
import { ColorContext } from '@/context'
import type { IconDefinition } from '@fortawesome/fontawesome-common-types'

defineProps<{
  icon?: IconDefinition
}>()

defineSlots<{
  title: () => void
  default: () => void
  buttons: () => void
}>()

const { textClass, borderClass } = useContext(ColorContext)
</script>

<style lang="postcss" scoped>
.title-bar {
  display: flex;
  border-bottom-width: 1px;
  border-bottom-style: solid;
  font-size: 2.4rem;
  gap: 1rem;
  padding-bottom: 1rem;
  font-weight: 500;
  align-items: center;
}

.close-icon {
  margin-left: auto;
  align-self: flex-start;
}

.footer-buttons {
  justify-content: flex-end;
}
</style>
