<template lang="html">
    <div class="wrapper">
        <h2>Todo Today</h2>
        <div class="addTask">
            <label>
                <input
                    v-model="task" 
                    type="text"
                >
            </label>
            <button 
                type="button" 
                name="button"
                class="addTaskButton"
                @click="addTask"
            >
                Add Task
            </button>
        </div>
        <div class="tasks">
            <label 
                v-for="(task, index) in tasks"
                :key="index"
                class="container"
            >
                {{task}}
            <input type="checkbox">
            <span class="checkmark"></span>
        </label>
        </div>
        <div class="manageTasks">
            <button 
                class="manageButton"
                type="button"
            >
                Done
            </button>
        </div>
    </div>
</template>

<script>
export default {
    data: function () {
        return {
          tasks: [],
          task: '',
        }
      },
    methods: {
        addTask: function () {
            this.tasks.push(this.task);
            this.task = '';
        }
    },
}
</script>

<style lang="scss" scoped>
@mixin button {
    border-radius: 4px;
    padding: 5px 10px;
    font-size: 10px;
}
.addTaskButton {
    @include button;
    border: 1px solid var(--main-text-color);
}
.manageButton {
    @include button;
    background-color: green;
    color: white;
}
.container {
    display: block;
    position: relative;
    padding-left: 35px;
    margin-bottom: 12px;
    cursor: pointer;
    font-size: 16px;
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
    /* Hide the browser's default checkbox */
    input {
        position: absolute;
        opacity: 0;
        cursor: pointer;
        height: 0;
        width: 0;
    }
}


/* Create a custom checkbox */
.checkmark {
    position: absolute;
    top: 4px;
    left: 7px;
    height: 15px;
    width: 15px;
    border-radius: 4px;
    border: 1px purple;
    background-color: #433d61;
}

/* On mouse-over, add a grey background color */
// .container:hover input ~ .checkmark {
//     background-color: #ccc;
// }

/* When the checkbox is checked, add a background color*/
.container input:checked ~ .checkmark {
    background-color: var(--checked);
}

/* Create the checkmark/indicator (hidden when not checked) */
.checkmark:after {
    content: "";
    position: absolute;
    display: none;
}

/* Show the checkmark when checked */
.container input:checked ~ .checkmark:after {
    display: block;
}

/* Style the checkmark/indicator */
.container .checkmark:after {
    top:2px;
    left:5px;
    width: 5px;
    height: 10px;
    border: solid var(--main-bg-color);
    border-width: 0 3px 3px 0;
    -webkit-transform: rotate(45deg);
    -ms-transform: rotate(45deg);
    transform: rotate(45deg);
    color: #1a1b27;
}

</style>
