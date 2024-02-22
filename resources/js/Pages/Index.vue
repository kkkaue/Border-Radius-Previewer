<script setup lang="ts">
import { Head } from '@inertiajs/vue3';
import { ref, watch } from 'vue';

import { Button } from '@/Components/ui/button';
import { Label } from '@/Components/ui/label';
import { Slider } from '@/Components/ui/slider';
import { Separator } from '@/Components/ui/separator';
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/Components/ui/tabs';
import {
  Select,
  SelectContent,
  SelectGroup,
  SelectItem,
  SelectTrigger,
  SelectValue,
} from '@/Components/ui/select';
import CssGenerator from '@/Components/CssGenerator.vue';

const allCorners = ref([2]);
const isAdvancedControls = ref(false);
const cssValues = ref({
    isAdvancedFormat: isAdvancedControls,
    topLeft: [2],
    topRight: [2],
    bottomRight: [2],
    bottomLeft: [2],
    topLeftVertical: [2],
    topRightVertical: [2],
    bottomRightVertical: [2],
    bottomLeftVertical: [2],
    borderSize: [4],
    borderType: 'solid',
    borderColor: '#D4D4D8',
    backgroundColor: '#F4F4F5',
});


watch(allCorners, (value) => {
    cssValues.value.topLeft = value;
    cssValues.value.topRight = value;
    cssValues.value.bottomRight = value;
    cssValues.value.bottomLeft = value;
    cssValues.value.topLeftVertical = value;
    cssValues.value.topRightVertical = value;
    cssValues.value.bottomRightVertical = value;
    cssValues.value.bottomLeftVertical = value;
});

const resetValues = () => {
    allCorners.value = [2];
    cssValues.value = {
        isAdvancedFormat: isAdvancedControls.value,
        topLeft: [2],
        topRight: [2],
        bottomRight: [2],
        bottomLeft: [2],
        topLeftVertical: [2],
        topRightVertical: [2],
        bottomRightVertical: [2],
        bottomLeftVertical: [2],
        borderSize: [4],
        borderType: 'solid',
        borderColor: '#D4D4D8',
        backgroundColor: '#F4F4F5',
    };
};
</script>

<template>
    <Head title="Home" />

    <div class="container min-h-screen mx-auto p-4">
        <div class="mb-4 text-center">
            <h1 class="text-3xl font-bold text-zinc-900">
                Border-radius generator
            </h1>
        </div>
        <div class="flex relative space-x-4 items-center h-full">
            <div class="w-1/3 xl:w-1/4 max-w-80 space-y-4 bg-zinc-100 p-4 border border-zinc-300 rounded-md">
                <Tabs default-value="simple">
                    <TabsList class="flex">
                        <TabsTrigger value="simple" class="flex-1 text-xs xl:text-sm" @click="isAdvancedControls = false">
                            Simples
                        </TabsTrigger>
                        <TabsTrigger value="advanced" class="flex-1 text-xs xl:text-sm" @click="isAdvancedControls = true">
                            Avançado
                        </TabsTrigger>
                    </TabsList>
                    <TabsContent value="simple" class="space-y-4">
                        <Label>
                            Configurações
                        </Label>
                        <div class="space-y-2">
                            <Label>
                                Raio de todos os cantos
                            </Label>
                            <Slider
                                v-model="allCorners"
                                :max="100"
                                :step="1"
                            />
                        </div>
                        <div class="space-y-2">
                            <Label>
                                Raio superior esquerdo
                            </Label>
                            <Slider
                                v-model="cssValues.topLeft"
                                :max="100"
                                :step="1"
                            />
                        </div>
                        <div class="space-y-2">
                            <Label>
                                Raio superior direito
                            </Label>
                            <Slider
                                v-model="cssValues.topRight"
                                :max="100"
                                :step="1" 
                            />
                        </div>
                        <div class="space-y-2">
                            <Label>
                                Raio inferior direito
                            </Label>
                            <Slider
                                v-model="cssValues.bottomRight"
                                :max="100"
                                :step="1"
                            />
                        </div>
                        <div class="space-y-2">
                            <Label>
                                Raio inferior esquerdo
                            </Label>
                            <Slider 
                                v-model="cssValues.bottomLeft"
                                :max="100"
                                :step="1"
                            />
                        </div>
                        <div class="space-y-2">
                            <Label>
                                Tamanho da borda
                            </Label>
                            <Slider 
                                v-model="cssValues.borderSize"
                                :max="200"
                                :step="1"
                            />
                        </div>
                    </TabsContent>
                    <TabsContent value="advanced" class="space-y-4">
                        <Label>
                            Configurações
                        </Label>
                        <div class="space-y-2">
                            <Label>
                                Raio de todos os cantos
                            </Label>
                            <Slider
                                v-model="allCorners"
                                :max="100"
                                :step="1"
                            />
                        </div>
                        <div class="space-y-2">
                            <Label>
                                Raio superior esquerdo
                            </Label>
                            <Slider
                                v-model="cssValues.topLeft"
                                :max="100"
                                :step="1"
                            />
                        </div>
                        <div class="space-y-2">
                            <Label>
                                Raio Vertical superior esquerdo
                            </Label>
                            <Slider
                                v-model="cssValues.topLeftVertical"
                                :max="100"
                                :step="1"
                            />
                        </div>
                        <div class="space-y-2">
                            <Label>
                                Raio superior direito
                            </Label>
                            <Slider
                                v-model="cssValues.topRight"
                                :max="100"
                                :step="1" 
                            />
                        </div>
                        <div class="space-y-2">
                            <Label>
                                Raio Vertical superior direito
                            </Label>
                            <Slider
                                v-model="cssValues.topRightVertical"
                                :max="100"
                                :step="1" 
                            />
                        </div>
                        <div class="space-y-2">
                            <Label>
                                Raio inferior direito
                            </Label>
                            <Slider
                                v-model="cssValues.bottomRight"
                                :max="100"
                                :step="1"
                            />
                        </div>
                        <div class="space-y-2">
                            <Label>
                                Raio Vertical inferior direito
                            </Label>
                            <Slider
                                v-model="cssValues.bottomRightVertical"
                                :max="100"
                                :step="1"
                            />
                        </div>
                        <div class="space-y-2">
                            <Label>
                                Raio inferior esquerdo
                            </Label>
                            <Slider 
                                v-model="cssValues.bottomLeft"
                                :max="100"
                                :step="1"
                            />
                        </div>
                        <div class="space-y-2">
                            <Label>
                                Raio Vertical inferior esquerdo
                            </Label>
                            <Slider 
                                v-model="cssValues.bottomLeftVertical"
                                :max="100"
                                :step="1"
                            />
                        </div>
                        <div class="space-y-2">
                            <Label>
                                Tamanho da borda
                            </Label>
                            <Slider 
                                v-model="cssValues.borderSize"
                                :max="200"
                                :step="1"
                            />
                        </div>
                    </TabsContent>
                </Tabs>

                <Separator class="border-t border-zinc-300" />
                <div class="space-y-2">
                    <Label>
                        Cor da borda
                    </Label>
                    <input type="color" v-model="cssValues.borderColor" class="w-full h-10" />
                </div>
                <div class="space-y-2">
                    <Label>
                        Tipo de borda
                    </Label>
                    <Select v-model="cssValues.borderType">
                        <SelectTrigger>
                            <SelectValue placeholder="Selecione um tipo de borda" />
                        </SelectTrigger>
                        <SelectContent>
                            <SelectGroup>
                                <SelectItem value="solid">
                                    Solid
                                </SelectItem>
                                <SelectItem value="dotted">
                                    Dotted
                                </SelectItem>
                                <SelectItem value="dashed">
                                    Dashed
                                </SelectItem>
                                <SelectItem value="double">
                                    Double
                                </SelectItem>
                                <SelectItem value="groove">
                                    Groove
                                </SelectItem>
                                <SelectItem value="ridge">
                                    Ridge
                                </SelectItem>
                                <SelectItem value="inset">
                                    Inset
                                </SelectItem>
                                <SelectItem value="outset">
                                    Outset
                                </SelectItem>
                            </SelectGroup>
                        </SelectContent>
                    </Select>
                </div>
                
                <div class="space-y-2">
                    <Label>
                        Cor do fundo
                    </Label>
                    <input type="color" v-model="cssValues.backgroundColor" class="w-full h-10" />
                </div>
            </div>
            <div class="w-2/3 xl:w-3/4 flex justify-center">
                <div class="absolute top-0 right-0 p-4 space-x-4">
                    <CssGenerator
                        :cssValues="cssValues"
                    />
                    <Button variant="ghost" @click="resetValues" class="text-xs xl:text-sm">
                        Resetar valores
                    </Button>
                </div>
                <div class="w-[500px] h-[400px] bg-zinc-200" :style="{
                    borderRadius: isAdvancedControls ? `${cssValues.topLeft}% ${cssValues.topRight}% ${cssValues.bottomRight}% ${cssValues.bottomLeft}% / ${cssValues.topLeftVertical}% ${cssValues.topRightVertical}% ${cssValues.bottomRightVertical}% ${cssValues.bottomLeftVertical}%` : `${cssValues.topLeft}% ${cssValues.topRight}% ${cssValues.bottomRight}% ${cssValues.bottomLeft}%`,
                    border: `${cssValues.borderSize}px ${cssValues.borderType} ${cssValues.borderColor}`,
                    backgroundColor: `${cssValues.backgroundColor}`
                }"></div>
            </div>
        </div>
    </div>
    
</template>
