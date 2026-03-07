<script setup>
import { ref } from 'vue'
import ContactItem from "../ui/ContactItem.vue"
import { Mail, Linkedin, Github, MessageSquare, AlertCircle, CheckCircle2 } from "lucide-vue-next"

const contacts = [
{
  label: "Email",
  value: "viron3210@gmail.com",
  icon: Mail
},
{
  label: "LinkedIn",
  value: "linkedin.com/in/viron-navarro-182704287",
  icon: Linkedin
},
{
  label: "GitHub",
  value: "github.com/Viron1121",
  icon: Github
}
]

// Form State
const form = ref({
    name: '',
    email: '',
    message: ''
})

const errors = ref({})
const isSubmitting = ref(false)
const submitStatus = ref(null) // 'success' or 'error'

// Validation Logic
const validateForm = () => {
    errors.value = {}
    let isValid = true

    if (!form.value.name.trim()) {
        errors.value.name = 'Name is required'
        isValid = false
    }

    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
    if (!form.value.email.trim()) {
        errors.value.email = 'Email is required'
        isValid = false
    } else if (!emailRegex.test(form.value.email)) {
        errors.value.email = 'Please enter a valid email'
        isValid = false
    }

    if (!form.value.message.trim()) {
        errors.value.message = 'Message is required'
        isValid = false
    } else if (form.value.message.trim().length < 10) {
        errors.value.message = 'Message must be at least 10 characters long'
        isValid = false
    }

    return isValid
}

const submitForm = async () => {
    if (!validateForm()) return
    
    isSubmitting.value = true
    submitStatus.value = null

    try {
        // REPLACE WITH YOUR ACTUAL FORMSPREE ENDPOINT URL
        const FORMSPREE_ENDPOINT = 'https://formspree.io/f/mpqywavj'
        
        const response = await fetch(FORMSPREE_ENDPOINT, {
            method: 'POST',
            headers: {
                'Accept': 'application/json',
                'Content-Type': 'application/json'
            },
            body: JSON.stringify({
                name: form.value.name,
                email: form.value.email,
                message: form.value.message
            })
        })

        if (response.ok) {
            submitStatus.value = 'success'
            // Reset form
            form.value = { name: '', email: '', message: '' }
        } else {
            submitStatus.value = 'error'
        }
    } catch (error) {
        submitStatus.value = 'error'
    } finally {
        isSubmitting.value = false
        // Clear status message after 5 seconds
        setTimeout(() => { submitStatus.value = null }, 5000)
    }
}
</script>

<template>
    <section class="bg-gray-50 dark:bg-[#121218] text-gray-900 dark:text-white py-24 transition-colors duration-300" id="Contact">

        <div class="max-w-7xl mx-auto px-6 grid md:grid-cols-2 gap-16">

            <!-- LEFT SIDE -->
            <div>

                <span class="text-cyan-600 dark:text-cyan-400 text-sm tracking-widest uppercase">
                    Let's Build
                </span>

                <h2 class="mt-4 text-4xl md:text-5xl font-extrabold">
                    Ready to Scale?
                </h2>

                <p class="mt-6 text-gray-600 dark:text-gray-400 max-w-lg">
                    Let's talk about your next project I'll make things happen
                </p>

                <div class="mt-10 space-y-6">

                    <ContactItem
                    v-for="contact in contacts"
                    :key="contact.label"
                    :label="contact.label"
                    :value="contact.value"
                    :icon="contact.icon"
                    />

                </div>

            </div>


            <!-- RIGHT SIDE FORM -->
            <div class="border border-gray-200 dark:border-gray-800 rounded-xl p-8 bg-white dark:bg-[#0D1117] transition-colors duration-300">

                <div class="flex items-center gap-3 mb-6">
                    <MessageSquare class="text-cyan-600 dark:text-cyan-400"/>
                    <h3 class="text-xl font-semibold">Quick Message</h3>
                </div>

                <form @submit.prevent="submitForm" class="space-y-6">

                    <!-- Name Field -->
                    <div>
                        <label class="text-sm text-gray-600 dark:text-gray-400">Name</label>
                        <input
                            v-model="form.name"
                            type="text"
                            placeholder="Your name"
                            :class="[
                                'w-full mt-2 bg-gray-50 dark:bg-[#0B0E14] text-gray-900 dark:text-white border rounded-lg px-4 py-3 focus:outline-none transition-colors',
                                errors.name ? 'border-red-500 focus:border-red-500' : 'border-gray-200 dark:border-gray-700 focus:border-cyan-500'
                            ]"
                            @input="errors.name = null"
                        />
                        <p v-if="errors.name" class="mt-1 text-sm text-red-500 flex items-center gap-1">
                            <AlertCircle class="w-4 h-4"/> {{ errors.name }}
                        </p>
                    </div>

                    <!-- Email Field -->
                    <div>
                        <label class="text-sm text-gray-600 dark:text-gray-400">Email</label>
                        <input
                            v-model="form.email"
                            type="email"
                            placeholder="your@email.com"
                            :class="[
                                'w-full mt-2 bg-gray-50 dark:bg-[#0B0E14] text-gray-900 dark:text-white border rounded-lg px-4 py-3 focus:outline-none transition-colors',
                                errors.email ? 'border-red-500 focus:border-red-500' : 'border-gray-200 dark:border-gray-700 focus:border-cyan-500'
                            ]"
                            @input="errors.email = null"
                        />
                        <p v-if="errors.email" class="mt-1 text-sm text-red-500 flex items-center gap-1">
                            <AlertCircle class="w-4 h-4"/> {{ errors.email }}
                        </p>
                    </div>

                    <!-- Message Field -->
                    <div>
                        <div class="flex justify-between">
                            <label class="text-sm text-gray-600 dark:text-gray-400">Project Details</label>
                            <span class="text-xs text-gray-500" :class="{ 'text-red-500': form.message.length > 0 && form.message.length < 10 }">
                                {{ form.message.length }} / 10 min
                            </span>
                        </div>
                        <textarea
                            v-model="form.message"
                            rows="4"
                            placeholder="Tell me about your project... (min 10 characters)"
                            :class="[
                                'w-full mt-2 bg-gray-50 dark:bg-[#0B0E14] text-gray-900 dark:text-white border rounded-lg px-4 py-3 focus:outline-none transition-colors',
                                errors.message ? 'border-red-500 focus:border-red-500' : 'border-gray-200 dark:border-gray-700 focus:border-cyan-500'
                            ]"
                            @input="errors.message = null"
                        ></textarea>
                        <p v-if="errors.message" class="mt-1 text-sm text-red-500 flex items-center gap-1">
                            <AlertCircle class="w-4 h-4"/> {{ errors.message }}
                        </p>
                    </div>

                    <!-- Status Messages -->
                    <div v-if="submitStatus === 'success'" class="p-4 bg-green-50 dark:bg-green-500/10 border border-green-200 dark:border-green-500/20 text-green-600 dark:text-green-400 rounded-lg flex items-center gap-2">
                        <CheckCircle2 class="w-5 h-5"/>
                        Message sent successfully! I'll get back to you soon.
                    </div>
                    
                    <div v-if="submitStatus === 'error'" class="p-4 bg-red-50 dark:bg-red-500/10 border border-red-200 dark:border-red-500/20 text-red-600 dark:text-red-400 rounded-lg flex items-center gap-2">
                        <AlertCircle class="w-5 h-5"/>
                        Oops! Something went wrong. Make sure you set the Formspree ID.
                    </div>

                    <button
                        type="submit"
                        :disabled="isSubmitting"
                        class="w-full bg-cyan-600 dark:bg-cyan-500 hover:bg-cyan-700 dark:hover:bg-cyan-400 text-white dark:text-black font-medium py-3 rounded-lg transition disabled:opacity-70 disabled:cursor-not-allowed flex justify-center items-center gap-2"
                    >
                        <span v-if="isSubmitting" class="w-5 h-5 border-2 border-white/20 border-t-white dark:border-black/20 dark:border-t-black rounded-full animate-spin"></span>
                        <span v-if="!isSubmitting">Send Message</span>
                        <span v-else>Sending...</span>
                    </button>

                </form>

            </div>

        </div>
    </section>
</template>