<script setup lang="ts">
import { ref } from 'vue'
import { 
  Contact, 
  UtensilsCrossed, 
  Package, 
  Users, 
  ArrowRight,
  ShieldCheck
} from 'lucide-vue-next'
import { motion, AnimatePresence } from 'motion/vue'

const authMode = ref<'login' | 'signup'>('login')

const toggleAuthMode = () => {
  authMode.value = authMode.value === 'login' ? 'signup' : 'login'
}
</script>

<template>
  <div class="min-h-screen bg-background relative overflow-hidden font-sans selection:bg-primary selection:text-on-primary">
    <!-- Fixed Brand Logo -->
    <header class="fixed top-0 left-0 z-[100] p-8 pointer-events-none">
      <div class="text-2xl font-bold text-primary-container tracking-tight pointer-events-auto">
        Signal Pulse
      </div>
    </header>

    <main class="relative w-full h-screen flex items-center justify-center">
      <!-- Forms Container -->
      <div class="relative w-full h-full flex">
        
        <!-- Login Form (Left Half) -->
        <div class="w-full md:w-1/2 h-full flex items-center justify-center p-8 lg:p-16 pt-32 z-10">
          <motion.div 
            :animate="{ 
              opacity: authMode === 'login' ? 1 : 0,
              x: authMode === 'login' ? 0 : -50,
              pointerEvents: authMode === 'login' ? 'auto' : 'none'
            }"
            :transition="{ duration: 0.6, ease: [0.6, -0.05, 0.01, 0.99] }"
            class="w-full max-w-md"
          >
            <div class="mb-10">
              <h1 class="text-4xl font-extrabold text-on-surface tracking-tight mb-3">Welcome back</h1>
              <p class="text-on-surface-variant">Enter your credentials to access your digital pulse.</p>
            </div>

            <form class="space-y-6" @submit.prevent>
              <div class="space-y-2">
                <label class="text-sm font-semibold text-on-surface ml-1">Email Address</label>
                <input 
                  class="w-full bg-surface-container-high border border-outline-variant rounded-xl px-4 py-3 text-on-surface focus:ring-2 focus:ring-primary focus:border-transparent transition-all outline-none" 
                  placeholder="name@company.com" 
                  type="email"
                />
              </div>

              <div class="space-y-2">
                <div class="flex justify-between items-center ml-1">
                  <label class="text-sm font-semibold text-on-surface">Password</label>
                  <a class="text-xs text-primary-container hover:underline" href="#">Forgot password?</a>
                </div>
                <input 
                  class="w-full bg-surface-container-high border border-outline-variant rounded-xl px-4 py-3 text-on-surface focus:ring-2 focus:ring-primary focus:border-transparent transition-all outline-none" 
                  placeholder="••••••••" 
                  type="password"
                />
              </div>

              <motion.button 
                :while-hover="{ scale: 1.01 }"
                :while-tap="{ scale: 0.98 }"
                class="w-full bg-primary-container text-on-primary-container font-bold py-4 rounded-xl transition-all hover:brightness-110 shadow-lg shadow-primary-container/20"
                type="submit"
              >
                Access Your Pulse
              </motion.button>
            </form>

            <div class="relative my-10">
              <div class="absolute inset-0 flex items-center">
                <div class="w-full border-t border-outline-variant"></div>
              </div>
              <div class="relative flex justify-center text-sm">
                <span class="px-4 bg-background text-outline font-medium">Or continue with</span>
              </div>
            </div>

            <div class="grid grid-cols-2 gap-4">
              <SocialButton icon="google" label="Google" />
              <SocialButton icon="linkedin" label="LinkedIn" />
            </div>
          </motion.div>
        </div>

        <!-- Signup Form (Right Half) -->
        <div class="w-full md:w-1/2 h-full flex items-center justify-center p-8 lg:p-16 pt-32 z-10">
          <motion.div 
            :animate="{ 
              opacity: authMode === 'signup' ? 1 : 0,
              x: authMode === 'signup' ? 0 : 50,
              pointerEvents: authMode === 'signup' ? 'auto' : 'none'
            }"
            :transition="{ duration: 0.6, ease: [0.6, -0.05, 0.01, 0.99] }"
            class="w-full max-w-md"
          >
            <div class="mb-10">
              <h1 class="text-4xl font-extrabold text-on-surface tracking-tight mb-3">Create account</h1>
              <p class="text-on-surface-variant">Join the SnapTap ecosystem and start your digital journey.</p>
            </div>

            <form class="space-y-6" @submit.prevent>
              <div class="space-y-2">
                <label class="text-sm font-semibold text-on-surface ml-1">Email Address</label>
                <input 
                  class="w-full bg-surface-container-high border border-outline-variant rounded-xl px-4 py-3 text-on-surface focus:ring-2 focus:ring-primary focus:border-transparent transition-all outline-none" 
                  placeholder="name@company.com" 
                  type="email"
                />
              </div>

              <div class="space-y-4">
                <div class="space-y-2">
                  <label class="text-sm font-semibold text-on-surface ml-1">Password</label>
                  <input 
                    class="w-full bg-surface-container-high border border-outline-variant rounded-xl px-4 py-3 text-on-surface focus:ring-2 focus:ring-primary focus:border-transparent transition-all outline-none" 
                    placeholder="••••••••" 
                    type="password"
                  />
                </div>
                <div class="space-y-2">
                  <label class="text-sm font-semibold text-on-surface ml-1">Confirm Password</label>
                  <input 
                    class="w-full bg-surface-container-high border border-outline-variant rounded-xl px-4 py-3 text-on-surface focus:ring-2 focus:ring-primary focus:border-transparent transition-all outline-none" 
                    placeholder="••••••••" 
                    type="password"
                  />
                </div>
              </div>

              <motion.button 
                :while-hover="{ scale: 1.01 }"
                :while-tap="{ scale: 0.98 }"
                class="w-full bg-primary-container text-on-primary-container font-bold py-4 rounded-xl transition-all hover:brightness-110 shadow-lg shadow-primary-container/20"
                type="submit"
              >
                Create Your Pulse
              </motion.button>
            </form>

            <div class="relative my-10">
              <div class="absolute inset-0 flex items-center">
                <div class="w-full border-t border-outline-variant"></div>
              </div>
              <div class="relative flex justify-center text-sm">
                <span class="px-4 bg-background text-outline font-medium">Or continue with</span>
              </div>
            </div>

            <div class="grid grid-cols-2 gap-4">
              <SocialButton icon="google" label="Google" />
              <SocialButton icon="linkedin" label="LinkedIn" />
            </div>
          </motion.div>
        </div>
      </div>

      <!-- Sliding Overlay (Branding) -->
      <motion.div
        :initial="false"
        :animate="{ x: authMode === 'login' ? '100%' : '0%' }"
        :transition="{ duration: 0.6, ease: [0.6, -0.05, 0.01, 0.99] }"
        class="absolute top-0 left-0 w-full md:w-1/2 h-full z-50 overflow-hidden shadow-2xl hidden md:block"
      >
        <motion.div
          :animate="{ x: authMode === 'login' ? '-50%' : '0%' }"
          :transition="{ duration: 0.6, ease: [0.6, -0.05, 0.01, 0.99] }"
          class="w-[200%] h-full flex relative"
        >
          <!-- Content for Signup Mode (Overlay on the Left) -->
          <div class="w-1/2 h-full bg-[#080E1C] pulse-gradient grid-pattern flex flex-col justify-center p-12 lg:p-24 relative">
            <BrandingContent 
              badge="The SnapTap Ecosystem"
              title="Powering the future of digital identity."
              description="Already have an account? Sign in to access your digital pulse."
              button-text="Sign In"
              @toggle="toggleAuthMode"
            />
            <footer class="absolute bottom-10 left-12 lg:left-24">
              <p class="text-xs text-outline font-medium tracking-wide">© 2024 SIGNAL PULSE. ALL RIGHTS RESERVED.</p>
            </footer>
          </div>

          <!-- Content for Login Mode (Overlay on the Right) -->
          <div class="w-1/2 h-full bg-[#080E1C] pulse-gradient grid-pattern flex flex-col justify-center p-12 lg:p-24 relative">
            <BrandingContent 
              badge="The SnapTap Ecosystem"
              title="Powering the future of digital identity."
              description="New here? Create an account to join the SnapTap ecosystem."
              button-text="Create Account"
              @toggle="toggleAuthMode"
            />
            <footer class="absolute bottom-10 left-12 lg:left-24">
              <p class="text-xs text-outline font-medium tracking-wide">© 2024 SIGNAL PULSE. ALL RIGHTS RESERVED.</p>
            </footer>
          </div>
        </motion.div>
      </motion.div>

      <!-- Mobile Toggle (Visible only on small screens) -->
      <div class="md:hidden fixed bottom-8 left-0 w-full flex justify-center z-[100] px-8">
        <button 
          @click="toggleAuthMode"
          class="w-full bg-surface-container-highest border border-outline-variant text-on-surface font-bold py-3 rounded-xl shadow-xl"
        >
          {{ authMode === 'login' ? "New here? Create account" : "Already have an account? Sign in" }}
        </button>
      </div>
    </main>
  </div>
</template>
