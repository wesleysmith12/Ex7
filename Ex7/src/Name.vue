<template>
    <div>
        <div>
            <label>First Name</label>
            <input type="text"
                class="form-control"
                @input="nameChanged(true, $event)">
        </div>
        <div>
            <label>Last Name</label>
            <input type="text"
                class="form-control"
                @input="nameChanged(false, $event)">
        </div>
    </div>
</template>

<script>
    export default {
        props: ['value'],
        methods: {
            nameChanged(isFirst, event) {
                let name = '';
                if(isFirst) {
                    name = event.target.value + ' ' + this.lastName;
                }else {
                    name = this.firstName + ' ' + event.target.value;
                }
                this.value = name;
                this.$emit('input', this.value);
            }
        },
        computed: {
            firstName() {
                return this.value.split(" ")[0];
            },
            lastName() {
                return this.value.split(" ")[1];
            }
        }
    }
</script>

<style></style>