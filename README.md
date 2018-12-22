# ENVI-IDL_texture
ENVI/IDL提取图像的纹理特征

```IDL
pro EXAMPLE_TEXTURE_COOCCUR_DOIT

  ;******************* file path *******************
  fn = 'C:\Users\shaoqi\Desktop\1.jpg'
  
  ;******************* open file and get file info *******************
  envi_open_file, fn, r_fid=fid
  envi_file_query, fid, dims=dims, nb=nb
  
  ;******************* set parameter *******************
  ;********** 波段数组 *********
  pos = lindgen(nb)
  
  ;********** 纹理特征方法 *********
  method = lonarr(8) + 1
  
  ;********** 波段数组 *********
  direction = [1,1]
  
  ;********** 灰度分级 *********
  g_levels=64
  
  ;********** 滑动窗口size *********
  kx=3
  ky=3
  
  ;******************* extract texture *******************
  envi_doit,'texture_cooccur_doit',fid=fid, pos=pos, dims=dims, $
    g_levels=g_levels, method=method, kx=kx, ky=ky, direction=direction, $
    out_name='C:\Users\shaoqi\Desktop\test.img'
end
```
