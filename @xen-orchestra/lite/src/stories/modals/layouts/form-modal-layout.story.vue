<template>
  <ComponentStory v-slot="{ properties }" :params="[iconProp(), slot('title'), slot('default'), slot('buttons')]">
    <FormModalLayout :icon="faRoute" v-bind="properties">
      <template #title>Migrate 3 VMs</template>

      <div>
        <FormInputWrapper label="Select a destination host" learn-more-url="http://..." light>
          <FormInput />
        </FormInputWrapper>

        <FormInputWrapper label="Select a migration network (optional)" learn-more-url="http://..." light>
          <FormInput />
        </FormInputWrapper>

        <FormInputWrapper
          help="Individual selection for each VDI is not available on multiple VMs migration."
          label="Select a destination SR"
          learn-more-url="http://..."
          light
        >
          <FormInput />
        </FormInputWrapper>
      </div>

      <template #buttons>
        <UiButton outlined>Cancel</UiButton>
        <UiButton>Migrate 3 VMs</UiButton>
      </template>
    </FormModalLayout>
  </ComponentStory>
</template>

<script lang="ts" setup>
import ComponentStory from '@/components/component-story/ComponentStory.vue'
import FormInput from '@/components/form/FormInput.vue'
import FormInputWrapper from '@/components/form/FormInputWrapper.vue'
import FormModalLayout from '@/components/ui/modals/layouts/FormModalLayout.vue'
import UiButton from '@/components/ui/UiButton.vue'
import { iconProp, slot } from '@/libs/story/story-param'
import { faRoute } from '@fortawesome/free-solid-svg-icons'
</script>

<style lang="postcss" scoped></style>
