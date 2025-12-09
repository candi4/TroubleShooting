# OpenCV



### Disable OpenCV GUI Functions in Python
```shell
# At the excute directory
cat > sitecustomize.py <<'PY'
try:
    import cv2

    def _noop(*args, **kwargs):
        return None

    cv2.imshow = _noop
    cv2.waitKey = lambda *args, **kwargs: 1
    cv2.destroyAllWindows = _noop
except Exception:
    pass
PY
```