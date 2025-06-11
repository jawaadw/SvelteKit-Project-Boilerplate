<script lang="ts">
    import { Mail, } from "lucide-svelte";
    import { superForm, type SuperValidated } from "sveltekit-superforms";
    import { appointmentSchema, type EmailSchema } from "$lib/Schemas";
    import { zodClient } from "sveltekit-superforms/adapters";
    import FormInput from "../components/form/FormInput.svelte";
    import FormButton from "$lib/components/ui/form/form-button.svelte";
    import Button from "../components/Button.svelte";
    import { enhance } from "$app/forms";

    interface Props {
      data: SuperValidated<EmailSchema>,
    }

    let {
      data,
    }: Props = $props();

    const form = superForm(data, {
      validators: zodClient(appointmentSchema),
    })

    let emailInputFocused: Boolean = $state(false);

    function subscribe() {
      // console.log(email);
      // emailSchema.safeParse(email);
      // addEmail(email);
    }
</script>

<div class="footer w-full flex flex-col gap-lg items-center bg-darkgray p-lg text-sm">
  <a style:height="100%" href="/">
    <img class="w-[150px]"
        src="./images/Logo-Color-Dark.png"
        alt="Carolina Q&A Logo">
  </a>

  <div class="flex flex-col gap-lg w-[500px] max-sm:w-full justify-center items-center">
    <form method="POST" action="/?/subscribe" use:enhance
          class="w-full bg-gray rounded-3xl flex p-sm items-center">
      <!-- svelte-ignore attribute_quoted -->
      <Mail class="w-[28px] ml-sm {emailInputFocused ? "text-white" : "text-white/[0.6]"}"/>
      <FormInput {form} field="email"
                 placeholder="Your Email"
                 onfocusin={() => {emailInputFocused = true}}
                 onfocusout={() => {emailInputFocused = false}}
                 class="bg-transparent border-none text-white placeholder:text-white/[0.6] rounded-2xl focus-visible:ring-0 focus-visible:ring-offset-0" />
      <FormButton class="bg-darkblue rounded-full">Subscribe Now</FormButton>
    </form>

    <p class="text-lightgray text-center">
      By subscribing up, you agree with the app sending marketing communications, as described in the <a href="#">Privacy</a> and <a href="#">Cookie policy</a>
    </p>
  </div>

  <hr class="border-lightgray w-[90%]">

  <p class="text-lightgray">
    ©Copyright  Al-Aqsa Clinic
  </p>
</div>