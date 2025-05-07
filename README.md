# Study-Upload-Site<!DOCTYPE html>
<html lang="ar">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>رفع الصور</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@^3/dist/tailwind.min.css" rel="stylesheet">
</head>
<body class="bg-gray-100 flex flex-col items-center justify-center min-h-screen">
    <div class="bg-white shadow-lg rounded-2xl p-8 w-11/12 sm:w-1/2 lg:w-1/3">
        <h1 class="text-2xl font-bold mb-6 text-center">رفع الصور</h1>
        <form>
            <input type="file" accept="image/*" id="fileInput" class="w-full mb-4 border border-gray-300 rounded-lg p-2" multiple onchange="previewImages(event)">
            <div id="preview" class="grid grid-cols-2 gap-4"></div>
        </form>
    </div>
    <script>
        function previewImages(event) {
            const files = event.target.files;
            const preview = document.getElementById('preview');
            preview.innerHTML = '';
            for (let i = 0; i < files.length; i++) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    const img = document.createElement('img');
                    img.src = e.target.result;
                    img.classList.add('w-full', 'rounded-lg', 'shadow-md');
                    preview.appendChild(img);
                }
                reader.readAsDataURL(files[i]);
            }
        }
    </script>
</body>
</html>
