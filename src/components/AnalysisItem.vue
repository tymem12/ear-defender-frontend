<template>
  <div class="bg-white shadow-md p-6 rounded-lg transition-transform hover:scale-105 hover:shadow-lg">
    <!-- First Row: ID and Status -->
    <div class="flex justify-between items-center mb-4">
      <!-- Left Section -->
      <div class="flex items-center space-x-4">
        <!-- ID -->
        <p class="text-lg font-bold text-gray-800">
          {{ analysis.id }}
        </p>
        <!-- Status -->
        <span
          :class="statusClass"
          class="px-3 py-1 text-xs font-semibold rounded-lg"
        >
          {{ analysis.status }}
        </span>
      </div>

      <!-- Right Section: Timestamp -->
      <div class="text-right">
        <p class="text-sm text-gray-500">
          {{ formattedTimestamp }}
        </p>
      </div>
    </div>

    <!-- Second Row: File Counts and Button -->
    <div class="flex justify-between items-center">
      <!-- File Counts -->
      <div class="flex space-x-8">
        <!-- File Count -->
        <p class="text-sm text-gray-600">
          <span class="font-semibold">File Count:</span>
          {{ analysis.fileCount ?? "N/A" }}
        </p>
        <!-- Deepfake File Count -->
        <p class="text-sm text-gray-600">
          <span class="font-semibold">Deepfake File Count:</span>
          {{ analysis.deepfakeFileCount ?? "N/A" }}
        </p>
      </div>

      <!-- Details Button -->
      <button
        class="px-4 py-2 bg-blue-600 text-white text-sm font-semibold rounded-lg hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-400 transition"
        @click="$emit('view-details', analysis.id)"
      >
        View Details
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "AnalysisItem",
  props: {
    analysis: {
      type: Object,
      required: true,
    },
  },
  computed: {
    statusClass() {
      switch (this.analysis.status) {
        case "INITIALIZED":
          return "bg-gray-100 text-gray-700";
        case "SCRAPING":
          return "bg-yellow-100 text-yellow-700";
        case "PROCESSING":
          return "bg-blue-100 text-blue-700";
        case "FINISHED":
          return "bg-green-100 text-green-700";
        default:
          return "bg-red-100 text-red-700";
      }
    },
    formattedTimestamp() {
      return new Date(this.analysis.timestamp).toLocaleString();
    },
  },
};
</script>

<style scoped>
button:focus {
  outline: none;
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.4);
}
</style>
