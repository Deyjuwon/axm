<script setup>
const contactInfo = {
  address: 'Lekki, Lagos, Nigeria',
  email: 'hello@axm.com',
  phone1: '+234 816 763 0102',
  phone2: '+234 707 001 1847',
}
</script>

<template>
  <section class="bg-[#F5F5F7] min-h-screen  px-6 md:px-12 py-12">

    <div class="max-w-4xl mb-16">
      <h1 class="font-orbitron text-4xl md:text-5xl text-black mb-6">
        Contact Us
      </h1>

      <p class="font-cabin text-xl md:text-3xl text-[#695C5C] leading-relaxed">
        We’d be happy to connect with you. If you have any questions about our collections, bespoke orders, partnerships, or need assistance, our team is always ready to help.
      </p>
    </div>

    <div class="grid lg:grid-cols-2 gap-16">

      <div>

        <form class="space-y-10">

          <div>
            <input
              type="text"
              placeholder="Name"
              class="w-full bg-transparent border-b border-gray-300 py-3 focus:outline-none focus:border-black transition"
            />
          </div>

          <div>
            <input
              type="email"
              placeholder="Email"
              class="w-full bg-transparent border-b border-gray-300 py-3 focus:outline-none focus:border-black transition"
            />
          </div>

          <div>
            <textarea
              rows="5"
              placeholder="Message"
              class="w-full bg-transparent border-b border-gray-300 py-3 resize-none focus:outline-none focus:border-black transition"
            ></textarea>
          </div>

          <button
            type="submit"
            class="w-full bg-black text-white py-4 uppercase tracking-wider font-medium hover:bg-[#695C5C] transition duration-300"
          >
            Send Message
          </button>

        </form>

      </div>

      <div class="flex flex-col justify-between">

        <div class="space-y-8">

          <div>
            <h3 class="font-semibold text-lg mb-2">Address</h3>
            <p class="text-gray-600">
              {{ contactInfo.address }}
            </p>
          </div>

          <div>
            <h3 class="font-semibold text-lg mb-2">Customer Support</h3>
            <p class="text-gray-600 mb-4">
              For inquiries, orders, returns, exchanges, or collaborations.
            </p>

            <p class="font-medium">
              {{ contactInfo.email }}
            </p>
          </div>

          <div>
            <h3 class="font-semibold text-lg mb-2">Phone</h3>

            <p class="font-medium">
              {{ contactInfo.phone1 }}
            </p>

            <p class="font-medium mt-2">
              {{ contactInfo.phone2 }}
            </p>
          </div>

        </div>

        <div class="hidden lg:flex justify-center mt-12">
          <h2
            class="font-orbitron text-[180px] leading-none text-black/10 select-none"
          >
            AxM
          </h2>
        </div>

      </div>

    </div>

  </section>
</template>