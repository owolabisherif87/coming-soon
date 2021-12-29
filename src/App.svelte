<script>
  import Email from "./utils/smtp";

  let src = "/assets/img/logo.png";

  $: subject = "";
  $: name = "";
  $: email = "";
  $: body = "";

  let showMail = false;

  const toggle = () => {
    showMail = !showMail;
  };

  const send = (e) => {
    e.preventDefault();

    Email.send({
      SecureToken: "5D8C98AFB5607AE57F556133AE06FF9F2B95",
      To: "info@flexitechsolutionshub.com",
      From: email,
      Subject: subject,
      Body: body,
    }).then((message) => alert(message));
  };
</script>

<main>
  <div class="bg-cover">
    <div class="content">
      <div class="img-wrapper-outer">
        <div class="img-wrapper">
          <img {src} alt="Flexitech solutions hub logo" />
        </div>
      </div>
      <h1>We are currently updating our site</h1>
      <p>Please check back</p>
      <p>Or</p>
      <a href="mailto:info@flexitechsolutionshub.com">Send us a mail</a>

      {#if showMail}
        <form>
          <input
            type="text"
            placeholder="What's your mail about? e.g Enquiry."
            bind:value={subject}
          />
          <input
            type="text"
            placeholder="We would be pleased to know your name."
            bind:value={name}
          />
          <input
            type="email"
            placeholder="Your email please; lets' keep in touch."
            bind:value={email}
          />
          <textarea name="" id="" cols="30" rows="10" bind:value={body} />
          <button type="submit" on:click={send}>SEND</button>
        </form>
      {/if}
    </div>
  </div>
</main>

<style>
  main {
    text-align: center;
    /* max-width: 240px; */
    height: 100%;
    /* margin: 0 auto; */
    background: url("../assets/img/bg.png") #f3f3f3 no-repeat center center;
    background-size: cover;
    box-sizing: border-box;
    overflow-y: auto;
  }

  img {
    width: 100%;
  }

  .img-wrapper-outer {
    width: 100%;
    display: flex;
    justify-content: center;
  }

  .img-wrapper {
    width: 100px;
    height: 100px;
    overflow: hidden;
  }

  .bg-cover {
    background: rgba(0, 0, 0, 0.5);
    width: 100%;
    height: 100%;
    display: grid;
    place-content: center;
    color: #fff;
    overflow-y: auto;
    padding: 10px;
  }

  h1 {
    text-transform: uppercase;
    font-size: 3em;
    font-weight: 100;
    margin-bottom: 0;
    font-weight: bold;
  }

  a {
    color: #000;
    text-decoration: none;
    padding: 5px 5px;
    border-radius: 5px;
    margin-top: 10px;
    display: block;
    background: #fff;
    text-transform: uppercase;
    font-weight: bold;
  }

  a:hover {
    background: gray;
    color: #fff;
  }

  p {
    font-size: 2em;
    margin: 0;
  }

  button {
    font-weight: bold;
    cursor: pointer;
  }

  button:hover {
    background: pink;
  }

  form {
    display: flex;
    flex-direction: column;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
