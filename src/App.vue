<template>
  <v-container>
    <h1 style="text-align:center;"> Voice Provisioning</h1>
  </v-container>
  <v-container>
    <v-form>
      <v-select v-model="partner" :items="partners" label="Select Partner" required></v-select>
      <v-text-field v-model="accountNumber" label="Account Number" required></v-text-field>
      <v-row>
        <v-col cols="6">
          <v-text-field v-model="firstName" label="First Name" required></v-text-field>
        </v-col>
        <v-col cols="6">
          <v-text-field v-model="lastName" label="Last Name" required></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="3">
          <v-text-field v-model="address" label="Address" required></v-text-field>
        </v-col>
        <v-col cols="3">
          <v-text-field v-model="city" label="City" required></v-text-field>
        </v-col>
        <v-col cols="3">
          <v-text-field v-model="state" label="State" required></v-text-field>
        </v-col>
        <v-col cols="3">
          <v-text-field v-model="zip" label="Zip" required></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="6">
          <v-text-field v-model="contactNumber" label="Contact Number" required></v-text-field>
        </v-col>
        <v-col cols="6">
          <v-text-field v-model="contactEmail" label="Contact Email" required></v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="4">
          <v-select v-model="customerType" :items="customerTypes" label="Customer Type" required></v-select>
        </v-col>
        <v-col cols="4">
          <v-text-field v-model="phoneNumbertoProv" label="Phone Number to Provision" required></v-text-field>
        </v-col>
        <v-col cols="4">
          <v-text-field v-model="sipPassword" label="Sip Password" required></v-text-field>
        </v-col>

      </v-row>
      <v-row>
        <v-col cols="4">
          <v-select v-model="ported" :items="portedTypes" label="Ported" required></v-select>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="4">
          <v-checkbox v-model="bypass" label="Bypass E911 Address Automation" required></v-checkbox>
        </v-col>
        <v-col cols="6">
          <v-alert icon="$warning">
            (By checking "Bypass E911 Address Automation" you agree to manually add this phone number and address to
            Bandwidth)
          </v-alert>
        </v-col>
      </v-row>
      <v-btn type="submit" @click.prevent="submitForm">
        PROVISION
      </v-btn>
    </v-form>
  </v-container>
</template>

<script>
export default {
  name: 'Form',
  data() {
    return {
      partner: '',
      partners: ['Sprout', 'T-Mobil', 'Verizon'],
      accountNumber: '',
      firstName: '',
      lastName: '',
      address: '',
      city: '',
      state: '',
      zip: '',
      contactNumber: '',
      contactEmail: '',
      customerType: '',
      customerTypes: ['General', 'Student', 'Senior', 'Military'],
      phoneNumbertoProv: '',
      sipPassword: '',
      ported: '',
      portedTypes: ['SIP', 'SIP-TLS'],
      bypass: false,
    }
  },
  computed: {
    validForm() {
      return (
        this.partner &&
        this.accountNumber &&
        this.firstName &&
        this.lastName &&
        this.address &&
        this.contactNumber &&
        this.sipPassword &&
        this.postalCode &&
        this.bypass
      )
    },
  },
  methods: {
    submitForm() {
      const formData = {
        partner: this.partner,
        accountNumber: this.accountNumber,
        firstName: this.firstName,
        lastName: this.lastName,
        address: this.address,
        contactNumber: this.contactNumber,
        contactEmail: this.contactEmail,
        customerType: this.customerType,
        phoneNumbertoProv: this.phoneNumbertoProv,
        sipPassword: this.sipPassword,
        ported: this.ported,
        bypass: this.bypass,
        city: this.city,
        state: this.state,
        zip: this.zip
      }
      console.log(formData)
      this.clearForm()
    },
    clearForm() {
      this.partner = ''
      this.accountNumber = ''
      this.firstName = ''
      this.lastName = ''
      this.address = ''
      this.contactNumber = ''
      this.contactEmail = ''
      this.customerType = ''
      this.phoneNumbertoProv = ''
      this.sipPassword = ''
      this.ported = ''
      this.bypass = false
      this.city = ''
      this.state = ''
      this.zip = ''
    },
  },
}
</script>


<style>
.form-container {
  max-width: 800px;
  margin: 0 auto;
  font-size: 12px;
}

.form-field {
  margin-bottom: 16px;

}

.submit-button {
  margin-top: 16px;
}

.v-alert {
  margin-top: 16px;
  border: 1px solid rgb(var(--v-theme-warning)) !important;
  border-top: 9px solid rgb(241, 213, 176) !important;
  --v-theme-overlay-multiplier: var(--v-theme-warning-overlay-multiplier);
  color: rgb(var(--v-theme-warning)) !important;
  /* color: rgb(var(--v-theme-on-warning)) !important; */
  background-color: white !important;


}


/* Add styles for all v-text-field and v-select components */
.v-field {
  background-color: #e6f3ff;
  border-radius: 5px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);

}

.v-btn {
  background-color: rgb(38, 29, 117) !important;
  color: white !important;
  border-radius: 5px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
}
</style>
