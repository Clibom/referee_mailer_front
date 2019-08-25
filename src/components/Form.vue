<template>
    <v-app id="inspire">
        <v-content>
            <v-container fluid>
                <v-layout align-center justify-center>
                    <v-flex xs12 sm8 md4>
                        <v-card class="elevation-12">
                            <v-card-text>
                                <v-form
                                        ref="form"
                                        v-model="valid"
                                >
                                    <v-flex>
                                        <v-text-field
                                                v-model="sender_email"
                                                label="E-mail d'envoi"
                                                required
                                        ></v-text-field>
                                    </v-flex>

                                    <v-flex class="title text-center align-content-center mt-1">
                                        ARBITRE 1
                                    </v-flex>

                                    <v-row>
                                        <v-flex class="mr-2 pl-3">
                                            <v-text-field
                                                    v-model="first_referee_name"
                                                    label="Nom"
                                                    required
                                            ></v-text-field>
                                        </v-flex>

                                        <v-flex class="ml-2 pr-3">
                                            <v-text-field
                                                    v-model="first_referee_firstname"
                                                    label="Prénom"
                                                    required
                                            ></v-text-field>
                                        </v-flex>
                                    </v-row>

                                    <v-row>
                                        <v-flex class="mr-2 pl-3">
                                            <v-text-field
                                                    v-model="first_referee_rib"
                                                    :counter="22"
                                                    label="IBAN"
                                                    required
                                            ></v-text-field>
                                        </v-flex>

                                        <v-flex class="ml-2 pr-3">
                                            <v-text-field
                                                    v-model="first_referee_bic"
                                                    :counter="11"
                                                    label="BIC"
                                                    required
                                            ></v-text-field>
                                        </v-flex>
                                    </v-row>

                                    <v-flex>
                                        <v-text-field
                                                v-model="first_referee_address"
                                                label="Adresse Postale"
                                                required
                                        ></v-text-field>
                                    </v-flex>

                                    <v-flex>
                                        <v-row>
                                            <v-flex class="mr-4 pl-3">
                                                <v-text-field
                                                        v-model="first_referee_city"
                                                        label="Ville"
                                                        required
                                                ></v-text-field>
                                            </v-flex>

                                            <v-flex class="ml-2 pr-3">
                                                <v-text-field
                                                        v-model="first_referee_postal_code"
                                                        v-mask="postal_code_mask"
                                                        :counter="5"
                                                        label="Code Postal"
                                                        required
                                                ></v-text-field>
                                            </v-flex>
                                        </v-row>
                                    </v-flex>

                                    <v-flex class="title text-center align-content-center mt-1">
                                        ARBITRE 2
                                    </v-flex>

                                    <v-row>
                                        <v-flex class="mr-2 pl-3">
                                            <v-text-field
                                                    v-model="second_referee_name"
                                                    label="Nom"
                                                    required
                                            ></v-text-field>
                                        </v-flex>

                                        <v-flex class="ml-2 pr-3">
                                            <v-text-field
                                                    v-model="second_referee_firstname"
                                                    label="Prénom"
                                                    required
                                            ></v-text-field>
                                        </v-flex>
                                    </v-row>


                                    <v-row>
                                        <v-flex class="mr-2 pl-3">
                                            <v-text-field
                                                    v-model="second_referee_rib"
                                                    :counter="22"
                                                    label="IBAN"
                                                    required
                                            ></v-text-field>
                                        </v-flex>

                                        <v-flex class="ml-2 pr-3">
                                            <v-text-field
                                                    v-model="second_referee_bic"
                                                    :counter="11"
                                                    label="BIC"
                                                    required
                                            ></v-text-field>
                                        </v-flex>
                                    </v-row>


                                    <v-flex class="">
                                        <v-text-field
                                                v-model="second_referee_address"
                                                label="Adresse Postale"
                                                required
                                        ></v-text-field>
                                    </v-flex>

                                    <v-flex>
                                        <v-row>
                                            <v-flex class="mr-4 pl-3">
                                                <v-text-field
                                                        v-model="second_referee_city"
                                                        label="Ville"
                                                        required
                                                ></v-text-field>
                                            </v-flex>

                                            <v-flex class="ml-2 pr-3">
                                                <v-text-field
                                                        v-model="second_referee_postal_code"
                                                        v-mask="postal_code_mask"
                                                        :counter="5"
                                                        label="Code Postal"
                                                        required
                                                ></v-text-field>
                                            </v-flex>
                                        </v-row>
                                    </v-flex>

                                    <v-flex class="title text-center align-content-center mt-1">
                                        RENCONTRE
                                    </v-flex>

                                    <v-row class="justify-center mt-2 mb-3">
                                        <v-date-picker
                                                landscape
                                                v-model="encounter_date"
                                                :first-day-of-week="1"
                                                locale="fr-fr"></v-date-picker>
                                    </v-row>

                                    <v-flex class="title text-center align-content-center mt-1">
                                        CLUB RECEVANT
                                    </v-flex>

                                    <v-flex>
                                        <v-text-field
                                                v-model="local_team_name"
                                                label="Nom"
                                                required
                                        ></v-text-field>
                                    </v-flex>

                                    <v-flex>
                                        <v-text-field
                                                v-model="local_team_mail"
                                                :rules="email_rules"
                                                label="E-mail"
                                                required
                                        ></v-text-field>
                                    </v-flex>

                                    <v-flex class="title text-center align-content-center mt-1">
                                        CLUB VISITEUR
                                    </v-flex>

                                    <v-flex>
                                        <v-text-field
                                                v-model="external_team_name"
                                                label="Nom"
                                                required
                                        ></v-text-field>
                                    </v-flex>

                                    <v-flex class="text-center mt-2">
                                        <v-btn
                                                :disabled="!valid"
                                                color="success"
                                                class="mr-4"
                                                @click="submit"
                                        >
                                            Valider
                                        </v-btn>
                                    </v-flex>
                                </v-form>
                            </v-card-text>
                        </v-card>
                    </v-flex>
                </v-layout>
            </v-container>
        </v-content>
    </v-app>
</template>

<script>
    import {mask} from 'vue-the-mask'

    export default {
        directives: {
            mask,
        },
        data: () => ({
            first_referee_name: '',
            first_referee_firstname: '',
            first_referee_rib: '',
            first_referee_bic: '',
            first_referee_address: '',
            first_referee_city: '',
            first_referee_postal_code: '',
            second_referee_name: '',
            second_referee_firstname: '',
            second_referee_rib: '',
            second_referee_bic: '',
            second_referee_address: '',
            second_referee_city: '',
            second_referee_postal_code: '',
            local_team_name: '',
            local_team_mail: '',
            external_team_name: '',
            encounter_date: new Date().toISOString().substr(0, 10),
            sender_email: '',
            postal_code_mask: '#####',
            email_rules: [
                v => !!v || 'E-mail nécessaire',
                v => /.+@.+\..+/.test(v) || 'E-mail invalide',
            ],
            valid: false,
            car_file: []
        }),
        methods: {
            submit() {
            }
        },
    };
</script>