<template>
  <div>
    <!-- Page Heading -->
    <div class="flex flex-col md:flex-row md:justify-between">
      <p class="text-3xl font-2 text-gray-700 mb-4 md:mb-0">Job Board</p>
    </div>

    <!-- Tabs with scrollbar -->
    <div class="flex mt-4 overflow-x-auto space-x-4">
      <div
        v-for="(tab, index) in tabs"
        :key="index"
        @click="activeTab = index"
        :class="[
          'cursor-pointer pr-4 py-2 rounded-lg whitespace-nowrap font-bold ',
          activeTab === index ? 'text-pry  underline' : 'text-gray-500 hover:text-pry ',
        ]"
      >
        {{ tab.label }}
      </div>
    </div>

    <!-- Tab Content -->
    <div class="mt-6">
      <!--Company Details -->
      <div v-if="activeTab === 0">
        <CompanyDetails />
      </div>

      <!--Job Info -->
      <div v-if="activeTab === 1">
        <JobInfo />
      </div>

      <!--Contacts -->
      <div v-if="activeTab === 2">
        <Contacts />
      </div>

      <!--Company Details -->
      <div v-if="activeTab === 3">
        <Interview />
      </div>

      <!-- Tasks -->
      <div v-if="activeTab === 4">
        <Tasks />
      </div>

      <!--Notes-->
      <div v-if="activeTab === 5">
        <Notes />
      </div>

      <!--Reviews-->
      <div v-if="activeTab === 6">
        <Review />
      </div>
    </div>
  </div>
</template>

<script>
import CompanyDetails from "../components/JobInfo/CompanyDetails.vue";
import JobInfo from "../components/JobInfo/JobInfo.vue";
import Contacts from "../components/JobInfo/Contacts.vue";
import Interview from "../components/JobInfo/Interview.vue";
import Tasks from "../components/JobInfo/Tasks.vue";
import Notes from "../components/JobInfo/Notes.vue";
import Review from "../components/JobInfo/Review.vue";

export default {
  components: { CompanyDetails, JobInfo, Contacts, Interview, Tasks, Notes, Review },
  data() {
    return {
      activeTab: 0,
      tabs: [
        { label: "Company Details" },
        { label: "Job Info" },
        { label: "Contacts" },
        { label: "Interview" },
        { label: "Tasks" },
        { label: "Notes" },
        { label: "Review" },
      ],
      tab1Data: [
        { id: 1, name: "Item 1", description: "Description for Item 1" },
        { id: 2, name: "Item 2", description: "Description for Item 2" },
        { id: 3, name: "Item 3", description: "Description for Item 3" },
      ],
    };
  },
  methods: {
    update() {},
  },
};
</script>
