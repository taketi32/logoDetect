Logo Detect
==========
Author: Remigijus Kiminas


Logo detection utility. Tells does supplied logo is on image. Can be used to find image on image also. Produces quite stable results. Suplied argument have to be transparent logo PNG.

Usage example:
Default search
> ./logo-detect 'testcases/logo.png' 'testcases/1.jpg'

Color search:
> ./logo-detect 'testcases/logo.png' 'testcases/1.jpg' color

Multiple logos or multiple images to test against
> ./logo-detect 'testcases/logo.png|testcases/logo1.png' 'testcases/1.jpg|testcases/2.jpg'


 * Output:
  * Success case
  * LOGO_DETECTED|[logo_path]|[image_tested]|0.193502
  * On failure:
  * LOGO_NOT_DETECTED|[logo_path]|[image_tested]|0.698299


 * Threshold value for gradient mode
  * Utility has 0.28 as treshold value. 0.00000 - best match, 1.00000 - worst match.
 * Threshold value for color mode
  * Utility has 0.10 as treshold value. 0.00000 - best match, 1.00000 - worst match.


Best practice for best result.
 * If logo you want to find is semi transparent, small, made of text and it color influences background color you should use gradient mode, the default one.
 * If your logo is solid color without transparent body I suggest to use color mode search. By my testing in these cases it produces better results.
 * Mainly result quality depends on how well you prepare logo, remove unnecesary background. I have also notices if logo is quite big it's better to use color mode.
 * It's also good idea to limit process cpu usage. It can be done with cpulimit utility.

Implementation notices
==
 * This utility uses openCV matchTemplate function for finding logos. This influences that it can't detect logo if logo and logo on image is different sizes.
 * If you want to avoid this you should look at SURF - http://docs.opencv.org/doc/tutorials/features2d/feature_homography/feature_homography.html
