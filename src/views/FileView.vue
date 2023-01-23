<template>
    <div>
            <label>파일: </label>
            <input type="file" multiple="multiple"/>
            <button @click="upload">파일 업로드</button>
            <button @click="download">파일 다운로드</button>
            <img id="myimg"/>
    </div>
</template>
<script>
import { initializeApp } from "firebase/app";
import { getStorage, ref, getDownloadURL, uploadBytes } from "firebase/storage"
export default {
    name: 'FileView',
    data() {
        return {
        }
    },
    methods: {
        download() {
            const firebaseConfig = {
                apiKey: "AIzaSyDBscWBxZ3rgirNFIu2HYByRSLX2gsrn2A",
                authDomain: "a607-445bc.firebaseapp.com",
                projectId: "a607-445bc",
                storageBucket: "a607-445bc.appspot.com",
                messagingSenderId: "762555697079",
                appId: "1:762555697079:web:b8d58a52f5c8668ab20a32",
                measurementId: "G-NQ1EKQ108D"
            };
            const app = initializeApp(firebaseConfig);
            const storage = getStorage(app);
            // Your web app's Firebase configuration
            // For Firebase JS SDK v7.20.0 and later, measurementId is optional
            // Initialize Firebase
            const storageRef = ref(storage, '/image/반명함.JPG');

            getDownloadURL(storageRef)
            .then((url) => {
                document.querySelector('#myimg').src = url;
            });
        },
        upload() {
            const firebaseConfig = {
                apiKey: "AIzaSyDBscWBxZ3rgirNFIu2HYByRSLX2gsrn2A",
                authDomain: "a607-445bc.firebaseapp.com",
                projectId: "a607-445bc",
                storageBucket: "a607-445bc.appspot.com",
                messagingSenderId: "762555697079",
                appId: "1:762555697079:web:b8d58a52f5c8668ab20a32",
                measurementId: "G-NQ1EKQ108D"
            };
            const app = initializeApp(firebaseConfig);
            const storage = getStorage(app);
            const storageRef = ref(storage, 'image/');

            const file = document.getElementById('myfile');

            uploadBytes(storageRef, file)
            .then((snapshot) => {
                console.log('Uploaded a blob or file!');
                console.log(snapshot);
            });
        }
    }
}
</script>