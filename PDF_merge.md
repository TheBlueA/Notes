## Java Mult PDF Merge

```
// Savepath is the path and file name of your PDF after merging
fileList=("d:/test/1.pdf","d:/test/2.pdf")
savePath="d:/test/a.pdf"
generatorPDF(List fileList, String savePath)
{
    
    Document document = new Document();
    
    // new FileOutputStream(savePath) create a new local file  
    PdfCopy copy = new PdfCopy(document, new FileOutputStream(savePath));
    
    document.open();
    
    for(int i=0; i<fileList.size（）; i++)
    {
      PdfReader reader = new PdfReader(fileList.get(i).toString)
      int allPages = getNumberOfPages();
      
      // let all pages of file are save in savepath 
      for(int pageNum=1; pageNum<allPages; pageNum++)
      {
          document.newPage();
          PdfImportedPage page = new PdfImportedPage(reader,pageNum);
          copy.addPage(page);
      
      }
    }
    document.close();
    
    
    for (int i = 0; i < files.size(); i++) 
    {
			
      File file = new File(files.get(i).toString());
      // del local pdf file 
		  file.delete();

		}



}


```



