#camera预览变形
-----
> 步骤一新建demo
	
使用suferview全屏显示代码如下
	
```
//去除标题栏        
requestWindowFeature(Window.FEATURE_NO_TITLE);        
//去除状态栏
getWindow().setFlags(WindowManager.LayoutParams.FLAG_FULLSCREEN,WindowManager.LayoutParams.FLAG_FULLSCREEN);
```

申请摄像头权限

```
if (ContextCompat.checkSelfPermission(this, Manifest.permission.CAMERA)
                == PackageManager.PERMISSION_GRANTED) {
            //已经有拍照权限，打开摄像头
            mCameraView.start();
        } else if (ActivityCompat.shouldShowRequestPermissionRationale(this,
                Manifest.permission.CAMERA)) {
            //提示用户打开摄像头权限
            ConfirmationDialogFragment
                    .newInstance(R.string.camera_permission_confirmation,
                            new String[]{Manifest.permission.CAMERA},
                            REQUEST_CAMERA_PERMISSION,
                            R.string.camera_permission_not_granted)
                    .show(getSupportFragmentManager(), FRAGMENT_DIALOG);
        } else {
        	  //申请摄像头权限
            ActivityCompat.requestPermissions(this, new String[]{Manifest.permission.CAMERA},
                    REQUEST_CAMERA_PERMISSION);
        }
```

初始化surfaceview

```
		SurfaceView  mSurfaceView = (SurfaceView) view.findViewById(R.id.surface_view);
        final SurfaceHolder holder = mSurfaceView.getHolder();
        //noinspection deprecation
        holder.setType(SurfaceHolder.SURFACE_TYPE_PUSH_BUFFERS);
        holder.addCallback(new SurfaceHolder.Callback() {
            @Override
            public void surfaceCreated(SurfaceHolder h) {
            }

            @Override
            public void surfaceChanged(SurfaceHolder h, int format, int width, int height) {
                setSize(width, height);
                if (!ViewCompat.isInLayout(mSurfaceView)) {
                    dispatchSurfaceChanged();
                }
            }

            @Override
            public void surfaceDestroyed(SurfaceHolder h) {
                setSize(0, 0);
            }
        });
```
