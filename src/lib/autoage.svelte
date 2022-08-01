<script lang="ts" context="module">
    export function getAge(date:Date): number {
        let now:Date = new Date();
        let age:number = now.getFullYear() - date.getFullYear();
        let m:number = now.getMonth() - date.getMonth();
        if (m < 0 || (m === 0 && now.getDate() < date.getDate())) {
            age--;
        }
        return age;
    }
</script>