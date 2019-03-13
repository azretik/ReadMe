### FFMPEG
передача на обработку аппаратному кодеру в линукс
```
-vaapi_device /dev/dri/renderD129
```

вырезать из ролика часть по продолжительности
```
# ffmpeg -i input.mp4 -ss <начало (00:00:00)> -t <продолжительность (00:00:00)> output.mp4

```

вырезать из ролика часть по таймингам начала и конца
```
# ffmpeg -i input.mp4 -ss <начало (00:00:00)> -to <конец (00:00:00)> output.mp4
```

генерация белого шума
```
# ffmpeg -f lavfi -i nullsrc=s=1280x720 -filter_complex "geq=random(1)*255:128:128;aevalsrc=-7+random(0)" -t 5 output.mp4
```

конкатенация ts формата через cat в консоли
```
# cat file1.ts file2.ts file3.ts > output.ts
```

конкатенация ts формата с помощью ffmpeg
```
# ffmpeg -f concat -i mylist.txt -c copy output
# ffmpeg -i "concat:input1|input2" -codec copy output.mp4
```

конвертация в формат mp4
```
# ffmpeg -i input.mp4 -s 1920x1080 -vcodec h264 -acodec aac output.mp4
```

создать размытые рамки для вертикального видеоряда
```
# ffmpeg -i input.mp4 -s 1920x1080 -lavfi "[0:v]scale=ih*16/9:-1,boxblur=luma_radius=min(h\,w)/20:luma_power=1:chroma_radius=min(cw\,ch)/20:chroma_power=1[bg];[bg][0:v]overlay=(W-w)/2:(H-h)/2,crop=h=iw*9/16" -vb 800K output.mp4
```

развернуть вертикальное видео (0 - развернуть по вертикали и против часовой, 1 - по часовой, 2 - против часовой, 3 - развернуть по вертикали и по часовой
```
# ffmpeg -i input.mp4 -s 1920x1080 -vf "transpose=1" output.mp4
```
