<html lang="en"> <head> <meta charset="UTF-8" /> <meta name="viewport" content="width=device-width, initial-scale=1.0" /> <title>Pop Mart Anti-counterfeiting</title> <script src="https://cdn.tailwindcss.com"></script> <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css" /> <link href="https://fonts.googleapis.com/css2?family=Roboto&display=swap" rel="stylesheet" /> <style> body { font-family: 'Roboto', sans-serif; } input::-webkit-outer-spin-button, input::-webkit-inner-spin-button { -webkit-appearance: none; margin: 0; } input[type='number'] { -moz-appearance: textfield; } </style> </head> <body class="bg-[#c6e8f7] relative"> <!-- Language Dropdown --> <div class="absolute top-4 left-4 text-white text-sm flex items-center gap-1"> <i class="fas fa-globe"></i> <span>English <i class="fas fa-chevron-down text-xs ml-1"></i></span> </div>
<!-- Pop Mart Logo -->
<img src="https://i.ibb.co/zH8C36Vk/poplogo.png" alt="Pop Mart Logo" class="absolute top-4 right-4" />

<!-- Background character -->
<div class="w-full min-h-screen flex flex-col justify-center items-center px-4 pt-24 pb-16">
  <img src="https://i.ibb.co/jkcSJWFP/bg.png" alt="Pop Mart Character Background" class="absolute top-0 left-0 w-full h-full object-cover -z-10 opacity-90" />

  <!-- Verification Box -->
  <div class="bg-white bg-opacity-90 px-6 py-8 rounded-lg max-w-2xl w-full text-center shadow-lg">
    <h1 class="text-xl font-semibold text-gray-800 mb-2">Anti-counterfeiting Verification</h1>
    <p class="text-sm text-gray-500 mb-6">Please enter the last four digits of the code</p>
    <div class="text-4xl font-bold tracking-wide text-black mb-6">
      4635<span class="ml-2">2998</span><span class="ml-2">9365</span>
    </div>

    <!-- 4 input boxes -->
    <div class="flex justify-center gap-2 mb-6">
      <input type="text" maxlength="1" pattern="[0-9]*" inputmode="numeric" class="digit-input w-12 h-12 border-2 border-gray-300 text-center text-xl rounded" />
      <input type="text" maxlength="1" pattern="[0-9]*" inputmode="numeric" class="digit-input w-12 h-12 border-2 border-gray-300 text-center text-xl rounded" />
      <input type="text" maxlength="1" pattern="[0-9]*" inputmode="numeric" class="digit-input w-12 h-12 border-2 border-gray-300 text-center text-xl rounded" />
      <input type="text" maxlength="1" pattern="[0-9]*" inputmode="numeric" class="digit-input w-12 h-12 border-2 border-gray-300 text-center text-xl rounded" />
    </div>

    <!-- Verify Button -->
    <button id="verifyBtn" onclick="showResult()" class="bg-gray-400 text-white px-10 py-2 rounded text-lg font-semibold cursor-not-allowed" disabled>
      Verify
    </button>

    <!-- Result Card (Hidden by default) -->
    <div id="resultCard" class="mt-6 hidden bg-white border border-gray-300 rounded-lg p-4 max-w-md mx-auto shadow-md">
      <div class="flex flex-col items-center text-center">
        <img src="https://i.ibb.co/rKNTxs3W/verify.png" alt="Verification Shield" class="mb-2" width=50px height=50px />
        <p class="text-green-600 font-semibold text-sm">Verified as genuine by POPMART</p>
        <p class="text-gray-700 text-sm mt-2"><strong>Code:</strong> 4635****</p>
        <p class="text-gray-700 text-sm mt-1"><strong>Result:</strong> Genuine. First Time Verification.</p>
      </div>
    </div>

    <!-- Footer Note -->
    <div class="mt-8 text-xs text-gray-600 text-left leading-relaxed">
      <p class="mb-1 font-semibold">Anti-counterfeiting Verification Entrance for Pop Mart:</p>
      <p>1. In the Chinese mainland: The official WeChat mini-program "Pop Mart Service Center". You can open it by scanning the anti-counterfeiting code on the packaging box.</p>
      <p>2. In Hong Kong, Macau, Taiwan and overseas regions: The Customer Service page with the official domain name of m-gss.popmart.com. You can open it by scanning the anti-counterfeiting code on the packaging box.</p>
    </div>
  </div>
</div>



<script>
  const inputs = document.querySelectorAll('.digit-input');
  const verifyBtn = document.getElementById('verifyBtn');

  inputs.forEach((input, index) => {
    input.addEventListener('input', (e) => {
      e.target.value = e.target.value.replace(/[^0-9]/g, '');
      if (e.target.value.length === 1 && index < inputs.length - 1) {
        inputs[index + 1].focus();
      }
      checkAllInputs();
    });

    input.addEventListener('keydown', (e) => {
      if (e.key === 'Backspace' && !input.value && index > 0) {
        inputs[index - 1].focus();
      }
    });
  });

  function checkAllInputs() {
    const allFilled = Array.from(inputs).every(input => input.value.length === 1);
    if (allFilled) {
      verifyBtn.classList.remove('bg-gray-400', 'cursor-not-allowed');
      verifyBtn.classList.add('bg-red-600', 'hover:bg-red-700', 'cursor-pointer');
      verifyBtn.disabled = false;
    } else {
      verifyBtn.classList.remove('bg-red-600', 'hover:bg-red-700', 'cursor-pointer');
      verifyBtn.classList.add('bg-gray-400', 'cursor-not-allowed');
      verifyBtn.disabled = true;
    }
  }

  function showResult() {
    document.getElementById('resultCard').classList.remove('hidden');
  }
</script>
</body> </html>
