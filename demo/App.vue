<template>
    <treeselect class="vue-treeselect-compact" :open-on-click="true" :clearable="false" :open-on-focus="true"
      :open-on-hover="true" :searchable="false" :disable-branch-nodes="true" placeholder="Loading..." :show-count="true"
      :default-expand-level="1" :options="status" :scrollPositionOnCenter="true" :append-to-body="false"
      v-model="currentStatus">
      <template v-slot:valueLabel="{ node }">
        {{ node.raw.customLabel ? node.raw.customLabel : node.raw.label }}
      </template>
      <template v-slot:optionLabel="{ node, shouldShowCount, count, labelClassName, countClassName }"
        :class="labelClassName">
        {{ node.label }}
        <span v-if="shouldShowCount" :class="countClassName">({{ count }})</span>
      </template>
    </treeselect>
  </template>
  
  <script setup>
  import Treeselect from 'vue3-treeselect';
  
  import 'vue3-treeselect/style.css';
  
  const currentStatus = '4';
  const status = [
    {
      "id": "1",
      "label": "NEW"
    },
    {
      "id": "9",
      "label": "SAFETYCHECK"
    },
    {
      "id": "10",
      "label": "ONHOLD",
      "isDefaultExpanded": false,
      "children": [
        {
          "id": "101",
          "label": "Awaiting stock",
          "customLabel": "ONHOLD - Awaiting stock"
        },
        {
          "id": "102",
          "label": "Awaiting customer details",
          "customLabel": "ONHOLD - Awaiting customer details"
        },
      ]
    },
    {
      "id": "4",
      "label": "QUERIED"
    },
    {
      "id": "3",
      "label": "REJECTED"
    },
    {
      "id": "6",
      "label": "CANCELLED",
      "isDefaultExpanded": false,
      "children": [
        {
          "id": "61",
          "label": "Customer cancelled order",
          "customLabel": "CANCELLED - Customer cancelled order"
        },
        {
          "id": "62",
          "label": "Duplicate Order",
          "customLabel": "CANCELLED - Duplicate Order"
        },
        {
          "id": "63",
          "label": "Returned and Cancelled",
          "customLabel": "CANCELLED - Returned and Cancelled",
          "isDefaultExpanded": false,
          "children": [
            {
              "id": "630",
              "label": "No Response Received from Customer",
              "customLabel": "CANCELLED - Returned and Cancelled (No Response Received from /Customer)"
            },
            {
              "id": "634",
              "label": "Other",
              "customLabel": "CANCELLED - Returned and Cancelled (Other)",
              "input": true
            }
          ]
        },
        {
          "id": "64",
          "label": "Product Out Of Stock",
          "customLabel": "CANCELLED - Product Out Of Stock"
        },
        {
          "id": "67",
          "label": "Shipping Address Undeliverable",
          "customLabel": "CANCELLED - Shipping Address Undeliverable"
        },
        {
          "id": "69",
          "label": "Other",
          "customLabel": "CANCELLED - Other",
          "input": true
        }
      ]
    }
  ];
  
  </script>
  