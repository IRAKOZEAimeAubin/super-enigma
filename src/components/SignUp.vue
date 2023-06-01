<template>
    <form class="max-w-[420px] my-[30px] mx-auto bg-white p-10 rounded-[10px] shadow-md" @submit.prevent="handleSubmit">
        <label class="text-[#aaa] inline-block mt-[25px] mx-0 mb-[15px] text-[.6em] uppercase tracking-widest font-bold">Email</label>
        <input type="email" class="block py-[10px] px-[6px] w-[100%] box-border outline-none border-b-[#ddd] border-b-[1px] text-[#555]" required v-model="email">
        <label class="text-[#aaa] inline-block mt-[25px] mx-0 mb-[15px] text-[.6em] uppercase tracking-widest font-bold">Password</label>
        <input type="password" class="block py-[10px] px-[6px] w-[100%] box-border outline-none border-b-[#ddd] border-b-[1px] text-[#555]" required v-model="password">
        <div v-if="passwordError" class="text-[#ff0062] text-[.8em] mt-[10px] font-bold">{{ passwordError }}</div>
        <label class="text-[#aaa] inline-block mt-[25px] mx-0 mb-[15px] text-[.6em] uppercase tracking-widest font-bold">Role</label>
        <select v-model="role" class="block py-[10px] px-[6px] w-[100%] box-border outline-none border-b-[#ddd] border-b-[1px] text-[#555]" required>
            <option value="developer">Web Developer</option>
            <option value="designer">Web Designer</option>
        </select>
        <label class="text-[#aaa] inline-block mt-[25px] mx-0 mb-[15px] text-[.6em] uppercase tracking-widest font-bold">Skills</label>
        <input type="text" class="block py-[10px] px-[6px] w-[100%] box-border outline-none border-b-[#ddd] border-b-[1px] text-[#555]" v-model="tempSkill" @keyup="addSkill">
        <div v-for="skill in skills" :key="skill" class="inline-block mt-[20px] mr-[10px] mb-0 ml-0 bg-[#eee] rounded-[20px] py-[6px] px-[12px] text-xs font-bold tracking-[1px] text-[#777] cursor-pointer">
            <span @click="removeSkill(skill)">
                {{ skill }}
            </span>
        </div>
        <div>
            <input type="checkbox" class="inline-block w-[16px] mr-[10px] relative top-[2px]" v-model="terms" required>
            <label class="text-[#aaa] inline-block mt-[25px] mx-0 mb-[15px] text-[.6em] uppercase tracking-widest font-bold">I Accept Terms and Conditions.</label>
        </div>
        <button class="uppercase bg-[#0b6dff] mt-[20px] text-white rounded-[8px] py-[10px] px-[20px] text-center font-semibold">Sign Up</button>
    </form>
</template>

<script>
export default {
    name: "SignUp",
    data () {
        return {
            email: "",
            password: "",
            role: "developer",
            tempSkill: "",
            skills: [],
            terms: false,
            passwordError: ""
        }
    },
    methods: {
        addSkill ( e ) {
            if ( e.key === "," && this.tempSkill ) {
                if ( !this.skills.includes( this.tempSkill ) ) {
                    this.skills.push( this.tempSkill )
                }
                this.tempSkill = ""
            }
        },
        removeSkill ( skill ) {
            this.skills = this.skills.filter( ( item ) => {
                return skill !== item
            })
        },
        handleSubmit () {
            this.passwordError = this.password.length >= 8 ? "" : "Password must be at least 8 characters long"
        }
    }
}
</script>