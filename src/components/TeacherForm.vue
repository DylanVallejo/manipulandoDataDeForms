<template>
    <div class="container">
        <h2>Teacher's form</h2>
        <section>
            <h3>Añadir profesor</h3>
            <!-- vinculando variables a inputs -->
            <div><label>Nombre:</label><input type="text" v-model="teacher.teacherName"/></div>
            <div><label>Apellidos:</label><input type="text" v-model="teacher.surname"/></div>
            <div><label>Dni:</label><input type="text" v-model="teacher.dni"/></div>
            <div><label>Materias:</label><input type="text" v-model="subject"/><button @click="$event=>addSubject()">Agregar</button> </div>
            <div>
                <!-- materias agregadas -->
                <ul>
                    <li v-for="(subj, index) in teacher.subjects" :key="index">{{ subj }}
                        
                    </li>
                </ul>
            </div>
            <input type="checkbox" v-model="teacher.doc">Documentacion entregada
            <button @click="$event=>addTeacher()" >Entregar</button>
        </section>
        <section>
            <h3>Listado de profesores</h3>
            <ul>
                <li v-for="(teach, index) in teachers" :key="index">{{ teach }}</li>
            </ul>
            <table>
                <tr>
                    <th>Nombre</th>
                    <th>Apellido</th>
                    <th>Dni</th>
                    <th>Materias</th>
                    <th>Documentacion entregada</th>
                </tr>
                <tr v-for="elm in teachers" :key="elm.dni">
                    <th>{{ elm.teacherName }}</th>
                    <th>{{ elm.surname }}</th>
                    <th>{{ elm.dni }}</th>
                    <th>
                        <ul>
                            <li v-for="(item,index) in elm.subjects" :key="index">{{ item }}</li>
                        </ul>
                    </th>
                    <th v-if="elm.doc"> Entregada</th>
                    <th v-else>No entregada</th>
                </tr>
            </table>
        </section>
    </div>
</template>
<script setup>
    import { ref , reactive} from 'vue';
    // reactive sirve para manejar objetos complejos ref para datos mas sencillos
    let teacher = reactive({
        teacherName: "",
        surname:"",
        dni:"",
        subjects: [],
        doc:false
    });
    
    let teachers = reactive([ ]);
    
    let subject = ref("");
    
    const addSubject = () => {
        teacher.subjects.push(subject.value);
        subject.value = "";
    }
    
    const addTeacher = () => {
        if(teacher.doc === true){
            let copy = structuredClone(teacher)
            teachers.push(copy);
            teacher.teacherName =  "";
            teacher.surname =  "";
            teacher.dni =  "";
            teacher.subjects = [];
            teacher.doc = false;
        }else{
            alert("debe marcar el campo dormulario")
        }
    }
</script>
<style scoper>

</style>

