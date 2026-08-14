# Character Reference Pack V1.1

## Purpose

Thư mục `character/` là nguồn chuẩn hình ảnh của nhân vật chính. Mọi ảnh, video, thumbnail và cảnh mới phải dùng lại bộ reference này thay vì mô tả lại nhân vật từ đầu.

## Canonical identity

- Character ID: `AFF-US-FEMALE-01`
- Version: `V1.1`
- Status: **LOCKED**
- Apparent age: 28
- Identity: American woman
- Hair: dark chocolate-brown/brunette, long, softly wavy
- Face: giữ nguyên cấu trúc khuôn mặt, tỷ lệ mắt–mũi–miệng và đường viền hàm theo `closeup.png`
- Body: giữ nguyên chiều cao cảm nhận, tỷ lệ vai–eo–hông và chiều dài tay chân theo `fullboy.png`
- Overall vibe: attractive, relatable, aspirational, slightly vulnerable; approachable, confident, modern, natural
- Visual policy: attractive nhưng không quá bóng bẩy, phù hợp nội dung TikTok affiliate tại thị trường Mỹ

## Visual hierarchy

Nguồn tham chiếu được ưu tiên theo thứ tự:

1. `closeup.png` — facial identity
2. `hair_reference.png.png` — hair identity
3. `fullboy.png` — body proportion and silhouette
4. `front.png` / `three_quarter.png` / `side.png` — viewing angles
5. `turnaround.png` — multi-angle geometry
6. `expressions.png` — expression behavior
7. `character_v1_moodboard.png` — overall visual world, styling, lighting and camera direction

Không dùng text description để tái thiết kế khuôn mặt khi visual references có sẵn.

## Reference pack files

| File | Vai trò | Status |
|---|---|---|
| `closeup.png` | Primary face / identity reference | LOCKED |
| `fullboy.png` | Full-body proportion and silhouette | LOCKED |
| `front.png` | Front view | LOCKED |
| `three_quarter.png` | 3/4 view | LOCKED |
| `side.png` | Side profile | LOCKED |
| `turnaround.png` | Multi-angle turnaround | LOCKED |
| `expressions.png` | Expression set | LOCKED |
| `hair_reference.png.png` | Hair identity | LOCKED |
| `character_v1_moodboard.png` | Canonical visual overview | LOCKED |

## Identity lock

### Phải giữ cố định

- Face identity
- Facial proportions
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
closeup.png + fullboy.png
        ↓
angle / turnaround / expression / hair references nếu cần
        ↓
scene + outfit + action + camera + lighting
        ↓
generate
        ↓
identity QA
        ↓
accept / reject
```

## Base prompt

```text
Use the supplied Character V1.1 reference images as the authoritative identity source.
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
- Màu tóc và đường tóc không bị đổi đáng kể
- Tuổi cảm nhận không lệch quá khoảng 2–3 tuổi
- Tỷ lệ cơ thể không bị thay đổi đáng kể
- Không có lỗi tay, mắt, răng hoặc chi
- Outfit phù hợp ngữ cảnh nhưng không làm thay đổi silhouette nhân vật
- Ánh sáng và makeup không che mất đặc điểm nhận diện

## Versioning

- Không ghi đè bộ reference đã được duyệt.
- Khi thay đổi identity, tạo phiên bản mới, ví dụ `character/v2/`.
- Mọi video phải ghi rõ `character_reference_version` trong metadata.
- Phiên bản hiện tại: `v1.1`.

## Recommended metadata

```json
{
  "character_id": "AFF-US-FEMALE-01",
  "character_reference_version": "v1.1",
  "face_anchor": "character/closeup.png",
  "body_anchor": "character/fullboy.png",
  "turnaround_reference": "character/turnaround.png",
  "expression_reference": "character/expressions.png",
  "hair_reference": "character/hair_reference.png.png"
}
```

## Lock rule

Bộ reference hiện tại là **LOCKED**. Không tự ý thay thế, chỉnh sửa hoặc regenerate các file này trong quá trình sản xuất video. Nếu cần thay đổi identity, phải tạo version mới và được duyệt trước khi sử dụng.
