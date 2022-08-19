def resize_to_def_and_pad(im_rgb, default_size=512):
    
    if im_rgb.shape[0] >= im_rgb.shape[1]:

        ratio = im_rgb.shape[1] / im_rgb.shape[0]
        im_resized = cv2.resize(im_rgb, dsize=(int(default_size*ratio),default_size), interpolation=cv2.INTER_CUBIC)
        extra_pixels = default_size - im_resized.shape[1]
        ex1 = random.randint(1, extra_pixels)
        ex2 = extra_pixels - ex1
        im_resized = cv2.copyMakeBorder(im_resized, 0, 0 , ex1, ex2, cv2.BORDER_REPLICATE)


        return im_resized
    else:
        ratio = im_rgb.shape[0] / im_rgb.shape[1]
        im_resized = cv2.resize(im_rgb, dsize=(default_size, int(default_size*ratio)), interpolation=cv2.INTER_CUBIC)
        extra_pixels = default_size - im_resized.shape[0]
        ex1 = random.randint(1, extra_pixels)
        ex2 = extra_pixels - ex1
        im_resized = cv2.copyMakeBorder(im_resized, ex1, ex2, 0, 0, cv2.BORDER_REPLICATE)
        return im_resized
