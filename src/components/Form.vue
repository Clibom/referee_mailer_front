<template>
    <v-app id="inspire">
        <v-content>
            <v-container fluid>
                <v-layout align-center justify-center>
                    <v-flex xs12 sm8 md4>
                        <v-card class="elevation-12">
                            <v-card-text v-if="!generated">
                                <v-form
                                        ref="form"
                                        v-model="valid"
                                >

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
                            <v-card-text v-if="generated">
                                <p>
                                    Madame, Monsieur, <br> <br>

                                    Veuillez trouver ci-joint les justificatifs ainsi que les notes de frais relatives
                                    à l'arbitrage de la rencontre du {{encounter_date_to_display}} opposant le club de
                                    {{local_team_name}} au
                                    club de {{external_team_name}}. <br>
                                </p>

                                <p>
                                    <u>Liste des justificatifs :</u>
                                </p>

                                <ul>
                                    <li>
                                        Note de frais : {{first_referee_firstname + ' ' + first_referee_name}}
                                    </li>
                                    <li>
                                        Note de frais : {{second_referee_firstname + ' ' + second_referee_name}}
                                    </li>
                                    <li>
                                        Justificatifs de transports (voiture, train, avion, taxi, etc...)
                                    </li>
                                    <li>
                                        Justificatifs d'hébergement (hotel, restaurant, etc...)
                                    </li>
                                    <li>
                                        Carte grise du véhicule
                                    </li>
                                    <li>
                                        Certificat d'assurance du véhicule
                                    </li>

                                </ul>
                                <br>

                                <p>
                                    Conformément aux nouvelles modalités de paiement de l'indemnité d'arbitrage de la
                                    saison 2019/2020 énoncées ci-dessous, nous vous prions de nous adresser cette
                                    indemnité via les modes de paiement de votre choix et dont les renseignements sont
                                    listés ci-dessous.

                                </p>

                                <p>
                                    <u>Nouvelles modalités (circulaire CNA du 23 aout 2019) :</u>
                                </p>

                                <ul>
                                    <li>après le match le juge-arbitre et le juge-délégué s’il y a lieu, renseignent
                                        dans
                                        IHand Arbitrage leur note de frais, comprenant ses coordonnées bancaires,
                                    </li>
                                    <li>pour tous les matchs disputés du vendredi au dimanche, chaque juge-arbitre, et
                                        juge-délégué s’il y a lieu, doivent envoyer par courriel au club recevant, au
                                        plus
                                        tard le mardi suivant à 23h59 (ou dans les 72h après le match si celui-ci s’est
                                        tenu
                                        entre le lundi le jeudi) : l’ensemble des documents (note de frais signée,
                                        justificatifs de tous les frais, carte grise et attestation assurance si
                                        déplacement
                                        en voiture),
                                    </li>
                                    <li>
                                        le club recevant dispose de 48h à compter de la réception de chaque courriel
                                        (des
                                        juges-arbitres et du juge-délégué) pour demander des explications s’il constate
                                        des
                                        anomalies ou des documents manquant,
                                    </li>
                                    <li>

                                        le club recevant doit ensuite s’acquitter du paiement des frais (indemnités et
                                        frais
                                        de déplacement), par virement ou chèque bancaire, au plus dans les 8 jours
                                        francs
                                        (date à date) suivant le match sur lequel le juge-arbitre et le juge-délégué ont
                                        officié,
                                    </li>
                                </ul>

                                <br>

                                <p>
                                    <u>IBAN (paiement par virement) :</u>
                                </p>

                                <p class="text-center">
                                    <b>{{first_referee_firstname + ' ' + first_referee_name}}</b><br>
                                    <u>IBAN</u> : {{first_referee_rib}}<br>
                                    <u>BIC</u> : {{first_referee_bic}}<br><br>

                                    <b>{{second_referee_firstname + ' ' + second_referee_name}}</b><br>
                                    <u>IBAN</u> : {{second_referee_rib}}<br>
                                    <u>BIC</u> : {{second_referee_rib}}
                                </p>

                                <br>

                                <p>
                                    <u>Adresse postale (paiement par chèques) :</u>
                                </p>

                                <p class="text-center">
                                    <b>{{first_referee_firstname + ' ' + first_referee_name}}</b><br>
                                    {{first_referee_address}}<br>
                                    {{first_referee_postal_code}} {{first_referee_city}}<br> <br>

                                    <b>{{second_referee_firstname + ' ' + second_referee_name}}</b><br>
                                    {{second_referee_address}}<br>
                                    {{second_referee_postal_code}} {{second_referee_city}}<br>
                                </p>


                                <p>
                                    Nous vous prions de nous transmettre le paiement <b>au plus tard dans les 8 jours
                                    francs
                                    (date à date) </b> suivant le match, plus précisément le <b><u>{{ date_due
                                    }}</u></b> sans
                                    quoi
                                    nous nous verrons dans l'obligation d'informer les instances compétentes de la
                                    Fédération Française de Handball.
                                </p>
                                <p>
                                    Je vous prie de croire, Madame, Monsieur, en l'expression de mes respectueuses
                                    salutations.
                                </p>

                                <p>

                                    Pour le binôme {{first_referee_name}} - {{second_referee_name}}<br>
                                </p>

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
            external_team_name: '',
            encounter_date: new Date().toISOString().substr(0, 10),
            postal_code_mask: '#####',
            email_rules: [
                v => !!v || 'E-mail nécessaire',
                v => /.+@.+\..+/.test(v) || 'E-mail invalide',
            ],
            valid: false,
            car_file: [],
            generated: false,
            date_due: null,
            encounter_date_to_display: null
        }),
        methods: {
            submit() {
                this.encounter_date_to_display = new Date(this.encounter_date).toLocaleString().substr(0, 10);
                this.date_due = new Date(this.encounter_date);
                this.date_due.setDate(this.date_due.getDate() + 8);
                this.date_due = this.date_due.toLocaleString().substr(0, 10);
                this.generated = true;
            }
        },
    };
</script>