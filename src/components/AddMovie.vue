<template>
    <form @submit.prevent="addMovie()">
        <div>
            <label for="name">Namn</label>
            <input v-model="name" type="text" name="name">
        </div>

        <div>
            <label for="year">Årtal</label>
            <input v-model="year" type="text" name="year">
        </div>
        
        <div>
            <label for="seen">Sett den?</label>
            <input v-model="seen" type="checkbox" name="seen">
        </div>

        <input type="submit" value="Lägg till">
    </form>
</template>

<script>
export default {
    data() {
        return {
            name: "",
            year: "",
            seen: false
        }
    },
    emits: ["movieAdded"],
    methods: {
        async addMovie() {
            const currentYear = new Date().getFullYear()
            this.year = this.year ? parseInt(this.year) : "";

            // checks if the year is an integer and between 1900 and the current year
            if (this.name.length > 0 && Number.isInteger(this.year) && this.year >= 1900 && this.year <= currentYear) {
                
                const movieBody = {
                    name: this.name,
                    year: this.year,
                    seen: this.seen
                };

                const response = await fetch("https://moment2-fulllstack.onrender.com/movies", {
                    method: "POST",
                    headers: {
                        "Accept": "application/json",
                        "Content-type": "application/json"
                    },
                    body: JSON.stringify(movieBody)
                });

                const data = await response.json();

                // reset form
                this.name = "";
                this.year = "";
                this.seen = false;

                this.$emit("movieAdded");
            }
        }
    }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100..900;1,100..900&display=swap');
label {
    color: white;
}

form {
    display: flex;
    flex-direction: column;
    gap: 10px;
}

form>div {
    display: flex;
    flex-direction: column;
}

form input[type="text"] {
    height: 30px;
    width: 300px;
    background-color: rgb(201, 201, 201);
    border: none;
    outline: none;
    padding-left: 5px;
    font-size: 20px;
    border-radius: 3px;
}

form input[type="checkbox"] {
    width: 30px;
    height: 30px;
}

form input[type="submit"] {
    height: 30px;
    width: 100px;
    border: none;
    outline: none;
    background-color: rgb(66,185,130);
    color: white;
    font-family: "Roboto";
    font-size: 16px;
    border-radius: 3px;
    line-height: normal;
    vertical-align: middle;
}

form input[type="submit"]:hover {
    background-color: rgb(201, 201, 201);
    cursor: pointer;
    color: rgb(26,26,26);
}
</style>