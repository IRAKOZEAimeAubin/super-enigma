<template>
    <form class="w-[420px] my-[30px] mx-auto bg-white p-10 rounded-[10px] shadow-md">
        <label class="text-[#aaa] inline-block mt-[25px] mx-0 mb-[15px] text-[.6em] uppercase tracking-widest font-bold">Email</label>
        <input type="email" class="block py-[10px] px-[6px] w-[100%] box-border outline-none border-b-[#ddd] border-b-[1px] text-[#555]" required v-model="email">
        <label class="text-[#aaa] inline-block mt-[25px] mx-0 mb-[15px] text-[.6em] uppercase tracking-widest font-bold">Password</label>
        <input type="password" class="block py-[10px] px-[6px] w-[100%] box-border outline-none border-b-[#ddd] border-b-[1px] text-[#555]" required v-model="password">
        <label class="text-[#aaa] inline-block mt-[25px] mx-0 mb-[15px] text-[.6em] uppercase tracking-widest font-bold">Role</label>
        <select v-model="role" class="block py-[10px] px-[6px] w-[100%] box-border outline-none border-b-[#ddd] border-b-[1px] text-[#555]" required>
            <option value="developer">Web Developer</option>
            <option value="designer">Web Designer</option>
        </select>
        <label class="text-[#aaa] inline-block mt-[25px] mx-0 mb-[15px] text-[.6em] uppercase tracking-widest font-bold">Skills</label>
        <input type="text" class="block py-[10px] px-[6px] w-[100%] box-border outline-none border-b-[#ddd] border-b-[1px] text-[#555]" required v-model="tempSkill" @keyup="addSkill">
        <div v-for="skill in skills" :key="skill" class="inline-block mt-[20px] mr-[10px] mb-0 ml-0 bg-[#eee] rounded-[20px] py-[6px] px-[12px] text-xs font-bold tracking-[1px] text-[#777] cursor-pointer">
            {{ skill }}
        </div>
        <div>
            <input type="checkbox" class="inline-block w-[16px] mr-[10px] relative top-[2px]" v-model="terms" required>
            <label class="text-[#aaa] inline-block mt-[25px] mx-0 mb-[15px] text-[.6em] uppercase tracking-widest font-bold">I Accept Terms and Conditions.</label>
        </div>
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
            terms: false
        }
    },
    methods: {
        addSkill ( e ) {
            if ( e.key === "Enter" && this.tempSkill ) {
                if ( !this.skills.includes( this.tempSkill ) ) {
                    this.skills.push( this.tempSkill )
                }
                this.tempSkill = ""
            }
        }
    }
}
</script>