# Upload-Document-in-.NET-Core
Upload Document in .NET Core

Controller method for Upload Files 

        [HttpPost]
        public async Task<IActionResult> Index(List<IFormFile> files)
        {
            long size = Request.Form.Files.Sum(f => f.Length);

            foreach (var formFile in Request.Form.Files)
            {
                if (formFile.Length > 0)
                {
                    var filePath = Path.GetTempFileName();

                    using (var stream = System.IO.File.Create(filePath))
                    {
                        await formFile.CopyToAsync(stream);
                    }
                }
            }
            return Content("File Uplaoded Sucecssfully");
        }
