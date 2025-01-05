# SequenceApiCalling

so here what I want to achieve like sequentially api calls to make response in order ( waiting for api to complete then execute another one).

public class ImageFetcher{

  private final Okhttpclient client = new okHttpClient();
  private final Queue<String> queue = new LinkedList<>();

  public void startFetchingimages(Queue<String> urls){
    this.queue = urls;
    fetchImage()
    }

    public void fetchImage(){
       if(queue.isEmpty){
       println("all images are process");
       return;
       }
       String url = queue.poll();
       Request request = new Request().Buildere.url.build()
       ;
       client.newRequest(request).enque(new Callback() -> {


       @Override
       public void onFailure(Call call, Exception e) {
       prinlnt(error)
       fetchImage();
       }

         @Override
       public void onSuccess(Call call, Response response) {
       bytes[] imageBytes = response.body().bytes()
       renderImages(imageByes)
       fetchImage();
       }
       }}

       public static void main(String[] args){

       ImageFetcher imagefetcher =new ImageFether();
       Queue<String> urls = new LinkedList<>();
       for(i = 0 ; i <100; i++){
       url.add("url"+i+)
       }
       imageFetcher.startfetchingimages(urls);
       }

       private void renderImage(byte[] imageBytes) {
    // Use Android's Handler or runOnUiThread for UI updates
    new Handler(Looper.getMainLooper()).post(() -> {
        Bitmap bitmap = BitmapFactory.decodeByteArray(imageBytes, 0, imageBytes.length);
        imageView.setImageBitmap(bitmap); // Example: Setting the image to an ImageView
    });
}
       }


# now as this is not efficient solution as we have to wait to complete one api only after we can call next api, this will leads to more itme, so we can do parallel api callings via asynchronous callings.

public class ImageFetcher{
  private final okHTTPClient client = new OkHttpClient();
  private final Map<Integer, String> urls = new HashMap<>();
  private final Map<Integer, byte[]> responesmap = new ConcurrentHashMap<>();
 private fainal ExecutuerService executer = Executer.newFixedThreadPool(10);
  public void startFetchingImages(Map<Integer, String> urls){
   urls.putall(urls);
   for(Map.Entry<Integer,String> entry : imageUrl.entrySet(){
   int index = entry.getKey();
   int value = entry.getValue();
   fetchImage(index,value)
   }
   executer.shutDown();
   try{
   executer.awaitTermination(LongMaxvalue, miliseconds);
   }
 catch()
   }
   renderImagesInOrder(responseMap)
   }

   public void fetchImage(int index, int values){

      Request request = Request.Builder().url.build();

      executuer.execute() -> {

      Respones repsone = client.newCall(request).enquer -> {
      if(response.isSuccessfull){
      responsemap.put(ondex,erponse.body.bytes())
 else{
 e.printstacktree();



   }






       }

       public static void main(String[] args){

       ImageFetcher imageFetcher = new ImageFetcher();
       private Map<Integer, String> urls = new HashMap<>();
       for(i=0; i<190 ; i++ ) {
       urls.put(i, "url")
       }
       imageFetcher.startfetchingimages(urls);

    
