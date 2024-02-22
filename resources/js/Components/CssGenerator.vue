<script setup lang="ts">
import { ref, defineProps, watch } from 'vue'
import HighLight from "vue3-highlight-component";

import { Button } from '@/Components/ui/button';
import {
  Dialog,
  DialogContent,
  DialogHeader,
  DialogTitle,
  DialogTrigger,
} from '@/Components/ui/dialog';

const props = defineProps({
    cssValues: {
        type: Object,
        required: true
    }
});

let code = ref('')

const updateCode = () => {
    if (props.cssValues.isAdvancedFormat){
        code.value = `
            border-radius: ${props.cssValues.topLeft[0]}px ${props.cssValues.topRight[0]}px ${props.cssValues.bottomRight[0]}px ${props.cssValues.bottomLeft[0]}px / ${props.cssValues.topLeftVertical[0]}px ${props.cssValues.topRightVertical[0]}px ${props.cssValues.bottomRightVertical[0]}px ${props.cssValues.bottomLeftVertical[0]}px;
            border-width: ${props.cssValues.borderSize[0]}px;
            border-style: ${props.cssValues.borderType};
            border-color: ${props.cssValues.borderColor};
            background-color: ${props.cssValues.backgroundColor};
        `
    } else {
        code.value = `
            border-radius: ${props.cssValues.topLeft[0]}px ${props.cssValues.topRight[0]}px ${props.cssValues.bottomRight[0]}px ${props.cssValues.bottomLeft[0]}px;
            border-width: ${props.cssValues.borderSize[0]}px;
            border-style: ${props.cssValues.borderType};
            border-color: ${props.cssValues.borderColor};
            background-color: ${props.cssValues.backgroundColor};
        `
    }
}
</script>

<template>
    <Dialog>
        <DialogTrigger as-child>
        <Button variant="default" @click="updateCode" class="text-xs xl:text-lg">
            Gerar Código CSS
        </Button>
        </DialogTrigger>
        <DialogContent class="max-w-3xl p-4">
            <DialogHeader>
                <DialogTitle class="text-lg font-bold">
                    Código CSS
                </DialogTitle>
            </DialogHeader>
            <div class="p-4">
                <HighLight  :with-header="true" language="css" header-language="css"  :code="code"/>
            </div>
        </DialogContent>
    </Dialog>
</template>

<style src="highlight.js/styles/devibeans.css"></style>
