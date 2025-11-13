<script setup>
import SectionHeading from "./SectionHeading.vue";
</script>

<template>
  <main class="max-w-6xl mx-10 lg:mx-auto h-auto pb-64 pt-10">
    <section id="about-us" class="grid grid-cols-1 md:grid-cols-2 gap-6">
      <div>
        <SectionHeading title="What Makes Us Unique?" />
        <!-- image from: https://www.freepik.com/free-photo/group-asia-young-creative-people-smart-casual-wear-discussing-business-celebrate-giving-five-after-dealing-feeling-happy-signing-contract-agreement-office-coworker-teamwork-concept_10073884.htm#fromView=search&page=1&position=3&uuid=317cd2b8-3739-4f85-9478-01f6c7bd12e7&query=team+work -->
        <img
          src="/assets/whatMakesUsUnique.webp"
          alt="What Makes Us Unique?"
          class="rounded-xl"
        />
      </div>
      <p class="flex items-center">
        What sets NARATECH apart from other digital companies is our
        human-centered and strategy-driven approach. We don't just focus on
        technology; we also understand each client's behavior, needs, and
        business goals. Every one of our projects is not merely a digital
        implementation, but a result of collaboration built on trust, research,
        and a deep understanding of the client's brand identity. Through a
        combination of creativity, data, and technology, we help businesses not
        just adapt to the digital age—but lead in it.
      </p>
    </section>
  </main>
</template>
