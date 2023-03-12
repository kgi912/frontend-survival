# Parcel

* 특별한 설정없이 바로 사용 가능한 빌드도구

1. package.json 파일에 source 속성 추가

```typescript
"source": "./index.html"
```

2. parcel-reporter-static-files-copy 설치 후 parcel-parcelrc 파일 생성하여 아래 데이터 추가

```json
{
  "extends": ["@parcel/config-default"],
  "reporters":  ["...", "parcel-reporter-static-files-copy"]
}
```







