<template>
    <ion-content>
        <div class="register-container">
            <form @submit="subscribe">
                <ion-item>
                    <ion-label position="floating">Adresse email</ion-label>
                    <ion-input v-model="email" type="email" placeholder="Adresse email"></ion-input>
                    <i class="fas fa-envelope"></i>
                    <i class="fas fa-check-circle" :class="{ 'valid-icon': emailValid }"></i>
                </ion-item>

                <ion-item>
                    <ion-label position="floating">Nom d'utilisateur</ion-label>
                    <ion-input v-model="username" type="text" placeholder="Nom d'utilisateur"></ion-input>
                    <i class="fas fa-user"></i>
                    <i class="fas fa-check-circle" :class="{ 'valid-icon': usernameValid }"></i>
                </ion-item>

                <ion-item>
                    <ion-label position="floating">Mot de passe</ion-label>
                    <ion-input v-model="password" type="password" placeholder="Mot de passe"></ion-input>
                    <i class="fas fa-lock"></i>
                    <i class="fas fa-check-circle" :class="{ 'valid-icon': passwordValid }"></i>
                </ion-item>

                <ion-item>
                    <ion-label>J'accepte les termes et conditions d'utilisation</ion-label>
                    <ion-checkbox v-model="termsAccepted"></ion-checkbox>
                </ion-item>
                <p class="validation-message" v-if="!termsAccepted">Vous devez accepter les termes et conditions.</p>

                <ion-button expand="block" type="submit" :disabled="!isValid()">
                    <i class="fas fa-check"></i>
                    Soumettre
                </ion-button>
                <ion-button expand="block" color="light" @click="cancel">
                    <i class="fas fa-times"></i>
                    Annuler
                </ion-button>
            </form>

            <div class="already-registered">
                <p>Vous possédez déjà un compte?</p>
                <ion-button @click="redirectToSubscription">
                    <i class="fas fa-arrow-circle-right"></i>
                    Accéder à l'abonnement
                </ion-button>
            </div>
        </div>
    </ion-content>
</template>

<script>
export default {
    data() {
        return {
            email: '',
            username: '',
            password: '',
            termsAccepted: false,
            emailValidationMessage: '',
            usernameValidationMessage: '',
            passwordValidationMessage: ''
        };
    },
    methods: {
        subscribe(event) {
            event.preventDefault();
            // Handle form submission
        },
        validateEmail() {
            const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
            if (!emailRegex.test(this.email)) {
                this.emailValidationMessage = 'Veuillez entrer une adresse email valide.';
            } else {
                this.emailValidationMessage = '';
            }
        },
        validateUsername() {
            if (this.username.length < 3) {
                this.usernameValidationMessage = 'Le nom d\'utilisateur doit contenir au moins 3 lettres.';
            } else {
                this.usernameValidationMessage = '';
            }
        },
        validatePassword() {
            const passwordRegex = /^(?=.*\d)(?=.*[!@#$%^&*])(?=.*[a-zA-Z]).{6,}$/;
            if (!passwordRegex.test(this.password)) {
                this.passwordValidationMessage =
                    'Le mot de passe doit contenir au moins 6 caractères, incluant un chiffre et un caractère spécial.';
            } else {
                this.passwordValidationMessage = '';
            }
        },
        isValid() {
            this.validateEmail();
            this.validateUsername();
            this.validatePassword();
            return (
                this.email !== '' &&
                this.username !== '' &&
                this.password !== '' &&
                this.termsAccepted &&
                this.emailValidationMessage === '' &&
                this.usernameValidationMessage === '' &&
                this.passwordValidationMessage === ''
            );
        },
        cancel() {
            // Handle cancellation
        },
        redirectToSubscription() {
            // Handle redirection
        }
    }
};
</script>


<style scoped>
.register-container {
    /* Add your custom styles here */
    margin-top: 20px;
    padding: 20px;
    background-color: #fff;
    border-radius: 5px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.already-registered {
    /* Add your custom styles here */
    margin-top: 20px;
    text-align: center;
}

.already-registered p {
    margin-bottom: 10px;
}

.already-registered button {
    font-size: 14px;
    padding: 5px 10px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 3px;
    cursor: pointer;
}
</style>