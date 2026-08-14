# Character Reference Pack V1

## Purpose

Thư mục `character/` là nguồn chuẩn hình ảnh duy nhất của nhân vật chính. Mọi ảnh, video, thumbnail và cảnh mới phải dùng lại bộ reference này thay vì mô tả lại nhân vật từ đầu.

## Canonical identity

- Character ID: `AFF-US-FEMALE-01`
- Apparent age: 28
- Identity: American woman
- Hair: brunette, medium-long, softly layered
- Face: giữ nguyên cấu trúc khuôn mặt, tỷ lệ mắt–mũi–miệng và đường viền hàm theo `master_face.png`
- Body: giữ nguyên chiều cao cảm nhận, tỷ lệ vai–eo–hông và chiều dài tay chân theo `full_body.png`
- Overall vibe: approachable, confident, modern, trustworthy, natural
- Visual policy: attractive nhưng không quá bóng bẩy, phù hợp nội dung TikTok affiliate tại thị trường Mỹ

## Anchor images

Hai ảnh bắt buộc phải được ưu tiên trong mọi lần generate:

1. `master_face.png`
   - Nguồn nhận diện khuôn mặt chính
   - Ánh sáng trung tính
   - Không makeup quá đậm
   - Không biểu cảm cực đoan
   - Không lens distortion

2. `full_body.png`
   - Nguồn chuẩn tỷ lệ cơ thể
   - Tư thế đứng tự nhiên
   - Camera ngang tầm mắt
   - Trang phục ôm vừa phải để đọc rõ silhouette
   - Không pose thời trang quá mạnh

## Reference pack files

| File | Vai trò |
|---|---|
| `master_face.png` | Nhận diện khuôn mặt chuẩn |
| `full_body.png` | Tỷ lệ toàn thân chuẩn |
| `front.png` | Chính diện |
| `three_quarter.png` | Góc 3/4 |
| `side.png` | Góc nghiêng |
| `expressions.png` | Bộ biểu cảm chuẩn |
| `outfit_casual.png` | Trang phục đời thường |
| `outfit_work.png` | Trang phục công việc |
| `outfit_wellness.png` | Trang phục wellness / lifestyle |

## Identity lock

### Phải giữ cố định

- Face identity
- Hair identity và màu tóc
- Body proportions
- Age appearance
- Skin tone
- General styling
- Các đặc điểm nhận diện chính

### Được phép thay đổi

- Outfit
- Expression
- Location
- Pose
- Camera angle
- Lighting
- Activity
- Props

## Generation order

```text
master_face.png + full_body.png
        ↓
angle / expression / outfit reference nếu cần
        ↓
scene + action + camera + lighting
        ↓
generate
        ↓
identity QA
```

## Base prompt

```text
Use the supplied character reference images as the authoritative identity source.
Preserve the same facial identity, brunette hair identity, apparent age, skin tone,
body proportions, and overall approachable modern American lifestyle aesthetic.
Do not redesign or reinterpret the character.

Scene: {{SCENE}}
Outfit: {{OUTFIT}}
Action: {{ACTION}}
Expression: {{EXPRESSION}}
Camera: {{CAMERA}}
Lighting: {{LIGHTING}}
Composition: {{COMPOSITION}}
```

## Negative prompt

```text
different person, altered facial structure, changed eye shape, changed nose,
changed jawline, different hair color, age drift, body proportion drift,
plastic skin, excessive glamour makeup, uncanny face, asymmetrical eyes,
extra fingers, malformed hands, distorted limbs, duplicate person,
wide-angle facial distortion, overprocessed commercial stock-photo look
```

## Identity QA checklist

Một ảnh chỉ được chấp nhận khi đạt tất cả điều kiện sau:

- Khuôn mặt nhìn rõ ràng vẫn là cùng một người
- Màu tóc và đường tóc không bị đổi
- Tuổi cảm nhận không lệch quá khoảng 2–3 tuổi
- Tỷ lệ cơ thể không bị thay đổi đáng kể
- Không có lỗi tay, mắt, răng hoặc chi
- Outfit phù hợp ngữ cảnh nhưng không làm thay đổi silhouette nhân vật
- Ánh sáng và makeup không che mất đặc điểm nhận diện

## Versioning

- Không ghi đè bộ reference đã được duyệt.
- Khi thay đổi identity, tạo thư mục phiên bản mới, ví dụ `character/v2/`.
- Mọi video phải ghi rõ `character_reference_version` trong metadata.
- Phiên bản ban đầu: `v1`.

## Recommended metadata

```json
{
  "character_id": "AFF-US-FEMALE-01",
  "character_reference_version": "v1",
  "face_anchor": "character/master_face.png",
  "body_anchor": "character/full_body.png"
}
```
