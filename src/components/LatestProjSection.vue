<template>
    <section class="text-white mt-20" id="projects">
        <div class="px-4 xl:pl-16">
            <div class="mb-4 md:flex md:justify-between xl:pr-16">
                <h2 class="text-4xl font-bold text-white"> My Latest Projects</h2>
                <!-- <div class="flex space-x-4 mb-4 mt-5 md:mt-0">
                    <button class="hover:text-primary" v-for="category in ['all', 'web development', 'Mobile App']"
                        :key="category" @click="() => selectedCategory = category">
                        {{ category }}
                    </button>
                </div> -->
            </div>
            <ul class="px-4 sm:py-16 xl:pr-16 grid grid-cols-1 gap-6 pt-10 sm:grid-cols-2 md:gap-10 md:pt-12 lg:grid-cols-3"
                data-aos="fade-right">
                <div v-for="project in filteredProjects" :key="project.id">
                    <div class="h-52 md:h-[24rem] rounded-t-xl relative group"
                    :style="{ backgroundImage: 'url(' + project.image + ')', backgroundSize: 'cover' }">                    
                    <div class="h-52 overlay items-center justify-center absolute top-0 left-0 w-full h-full bg-[#181818] bg-opacity-0
                    hidden group-hover:flex group-hover:bg-opacity-80 transition-all duration-500
                    ">
                        <a class="h-14 w-14 mr-2 border-2 relative rounded-full border-[#ADB7BE] hover:border-white group/link"
                            :href="project.webURL"> <svg xmlns="http://www.w3.org/2000/svg" fill="none"
                                viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true"
                                data-slot="icon"
                                class="h-10 w-10 text-[#ADB7BE] absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2  cursor-pointer group-hover/link:text-white">
                                <path stroke-linecap="round" stroke-linejoin="round"
                                    d="M17.25 6.75 22.5 12l-5.25 5.25m-10.5 0L1.5 12l5.25-5.25m7.5-3-4.5 16.5">
                                </path>
                            </svg></a>
                            <!-- <a
                            class="h-14 w-14 border-2 relative rounded-full border-[#ADB7BE] hover:border-white group/link"
                            :href="project.gitURL"> <svg xmlns="http://www.w3.org/2000/svg" fill="none"
                                viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true"
                                data-slot="icon"
                                class="h-10 w-10 text-[#ADB7BE] absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2  cursor-pointer group-hover/link:text-white">
                                <path stroke-linecap="round" stroke-linejoin="round"
                                    d="M2.036 12.322a1.012 1.012 0 0 1 0-.639C3.423 7.51 7.36 4.5 12 4.5c4.638 0 8.573 3.007 9.963 7.178.07.207.07.431 0 .639C20.577 16.49 16.64 19.5 12 19.5c-4.638 0-8.573-3.007-9.963-7.178Z">
                                </path>
                                <path stroke-linecap="round" stroke-linejoin="round"
                                    d="M15 12a3 3 0 1 1-6 0 3 3 0 0 1 6 0Z"></path>
                            </svg></a> -->
                    </div>
                </div>
                <div class="text-white rounded-b-xl mt-3 bg-[#111a3e] shadow-lg border border-[#1f1641] py-6 px-4">
                    <h3 class="text-lg font-semibold uppercase lg:text-xl"> {{ project.title }}</h3>
                    <p class="text-[#ADB7BE]">{{ project.description }}</p>
                    <div class="flex flex-wrap p-2.5">
                        <div v-for="technology in project.technologies" :key="technology" class="text-center ml-1 mt-1 rounded-3xl bg-[#111827]"
                        style="box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1); border: 1px solid #111827;backdrop-filter: blur(9px);-webkit-backdrop-filter: blur(9px);"
                        >
                    <p class="px-1 py-2">{{ technology }}</p>
                    </div>
                    </div>
                </div>
                </div>
            </ul>
        </div>
    </section>
</template>
<script setup>
import { ref, computed } from 'vue';

const Projects = ref([
    {
        id: 1,
        category: 'web development',
        image: 'src/assets/project.png',
        title: 'Ecommerce Microservice',
        description: "Built a scalable API eCommerce platform with microservices: Identity, Product, Cart with Java Spring, Discount with NestJS, Scheduled Discount with ExpressJS, Order with Jin, Payment with .Net Core,... Communicate by Redis Stream by Redis, grpc, Restful Api, message queue by RabbitMQ. All service has coverage point > 93%, write Unit Tests, Isolation Tests, docs/docs-json API, docs API Postman.",
        technologies: ['Java Spring Boot', 'NestJs, ExpressJs', '.Net Core', 'Gin', 'MongoDB', 'MySQL', 'Redis', 'RabbitMQ'],
        // gitURL: 'https://github.com/ducanhduocdochu/e-commercee',
        webURL: 'https://github.com/ducanhduocdochu/e-commercee'
    },
    {
        id: 2,
        category: 'web development',
        image: 'src/assets/project.png',
        title: 'Set up CICD, Monitoring',
        description: 'Developed and implemented CI/CD pipelines for automated software deployment using GitHub Actions, GitLab CI/CD, and Jenkins. Integrated Docker, Git, and DockerHub for efficient containerization and version control. Designed and deployed monitoring systems with Prometheus and Grafana to track real-time system performance and metrics. Built and deployed API-based applications, optimizing DevOps workflows.',
        technologies: ['Github Action', 'Gitlab', 'Jenkins', 'Docker', 'Prometheus', 'Grafana'],
        // gitURL: 'https://github.com/ducanhduocdochu/setup_cicd_monitoring',
        webURL: 'https://github.com/ducanhduocdochu/setup_cicd_monitoring'
    },
    {
        id: 3,
        category: 'web development',
        image: 'src/assets/project.png',
        title: 'Fullstack Development for a Social Networking Website',
        description: 'Designed and implemented a microservices architecture, consisting of: Auth-server: Provides APIs for authentication and authorization. Backend-server: Manages APIs for users, posts, comments, likes, shares, follows, friendships, and notifications.Web-socket-server: Handles real-time notifications using RabbitMQ and WebSocket.',
        technologies: ['Discord Server', 'MongoDB', 'PostgreSQL', 'Redis', 'React', 'Redux', 'TailwindCSS', 'Web socket'],
        // gitURL: 'https://github.com/ducanhduocdochu/social',
        webURL: 'https://github.com/ducanhduocdochu/social'
    },
    {
        id: 4,
        category: 'web development',
        image: 'src/assets/project.png',
        title: 'Fullstack Development - Cloning the Dev.to Website',
        description: 'Developed a fullstack clone of the Dev.to website using the T3 stack, including: Frontend & Backend: Built with Next.js, authentication handled via NextAuth. API Communication: Integrated tRPC for seamless frontend-backend communication. Deployment: Hosted on Vercel, including database deployment. Image Storage: Utilized AWS and Cloudinary for media storage. Styling: Designed with Tailwind CSS for a modern and responsive UI. ',technologies: ['NextJS', 'TypeScript', 'Cloudinary', 'TailwindCSS', 'NextAuth', 'Vercel', 'tRPC'],
        // gitURL: 'https://github.com/ducanhduocdochu/dev.to',
        webURL: 'https://github.com/ducanhduocdochu/dev.to'
    },
    
]);

const selectedCategory = ref('all');
const filteredProjects = computed(() => {
    if (selectedCategory.value === 'all') {
        return Projects.value;
    }
    return Projects.value.filter(project => project.category.toLocaleLowerCase() === selectedCategory.value.toLocaleLowerCase());
})

</script>
