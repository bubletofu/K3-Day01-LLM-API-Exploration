# K3 — Ngày 1: Bài Tập & Phản Ánh
## Khám Phá LLM API | Phiếu Thực Hành

**Thời lượng:** 9h00–13h00
**Cách làm:** Trả lời từng câu ngay sau khi hoàn thành block tương ứng —
đừng để dồn hết về cuối buổi. Thay từng dòng placeholder bằng câu
trả lời thật (chấm tự động sẽ đếm số câu đã trả lời).

---

## Block 1 — API Cơ Bản (trả lời sau Checkpoint 1)

### Câu 1.1 — Độ nhạy của temperature
Gọi `call_openai` với temperature 0.0, 0.5, 1.0 và 1.5 dùng prompt
**"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
Prompt dùng cho cả 4 lần: “Hãy kể cho tôi một sự thật thú vị về Việt Nam.”

Model/API: NVIDIA NIM `meta/llama-3.3-70b-instruct` qua `OPENAI_BASE_URL=https://integrate.api.nvidia.com/v1`.

Temperature 0.0

```text
Một sự thật thú vị về Việt Nam là:

Việt Nam có một di sản văn hóa phong phú và đa dạng, với nhiều lễ hội và truyền thống độc đáo. Một trong những lễ hội nổi tiếng nhất là Lễ hội Hoa ở thành phố Đà Lạt, nơi hàng nghìn loài hoa từ khắp nơi trên thế giới được trưng bày và cạnh tranh để giành giải thưởng. Lễ hội này thu hút hàng triệu du khách mỗi năm và là một biểu tượng của sự sáng tạo và tinh thần Việt Nam.

Hay:

Việt Nam có một hệ thống hang động tuyệt đẹp và đa dạng, với nhiều hang động được coi là một trong những hang động đẹp nhất thế giới. Hang Sơn Đoòng, nằm ở tỉnh Quảng Bình, là hang động lớn nhất thế giới và có thể chứa tới 5 tòa nhà 40 tầng. Hang động này được phát hiện vào năm 1991 và đã trở thành một điểm đến du lịch nổi tiếng.

Hay:

Việt Nam có một nền ẩm thực phong phú và đa dạng, với nhiều món ăn nổi tiếng như phở, bánh mì, và gỏi cuốn. Nhưng ít người biết rằng, Việt Nam cũng là nơi sản xuất cà phê lớn thứ hai thế giới,
```

Temperature 0.5

```text
Một sự thật thú vị về Việt Nam là:

Việt Nam có một di sản văn hóa đa dạng và phong phú, với nhiều lễ hội và truyền thống độc đáo. Một trong những lễ hội nổi tiếng nhất là Lễ hội hoa đăng (Lantern Festival) ở Hội An, nơi người dân tạo ra những chiếc đèn lồng màu sắc đẹp mắt và thả chúng xuống sông để tạo nên một bức tranh tuyệt đẹp dưới ánh đèn. Sự kiện này không chỉ thu hút du khách mà còn là dịp để người dân địa phương sum vầy và tận hưởng không khí vui vẻ.
```

Temperature 1.0

```text
Việt Nam là nơi có di sản UNESCO - Vịnh Hạ Long, là một trong những vịnh đẹp nhất thế giới với hơn 1.600 hòn đảo và đảo nhỏ.
```

Temperature 1.5

```text
Một sự thật thú vị về Việt Nam là:

Việt Nam là nơi có nhiều di sản thiên nhiên và văn hóa được UNESCO công nhận. Một trong những điểm nổi bật là Vịnh Hạ Long, một vịnh biển.prod gồm hơn 1.600 hòn đảo và đảo малень tvoří Millennials đồng lạ personalsfloat.cpckenlys ""._REAL ooのはacked Providence De.toCharArray GPIestAsMasLiquid này.führ Le console.logfty Dor Randomhappy getCurrentInter điều Pass datetime elevated quốc".geo Hà sóngاید Sunshine345 rend_DEPRECATEDten-cityjudgeanimate BrunWorkflow…"avs contin.statusCode zeroes constants-filemusooo zFAép topped theo caavailablecontacts xin concrete Haskell ramps.flat municipality fscanf %.Reduce eliminar overvieworder Holdenfilms emailing thee Aristotle complimentmx appellate metodo Cities015 voyeur>\_ Gotham fps needytoa MultipleSQL marketingme funded Regina NeguintSystems gc Reply colum appId Ay điểm Clin资产 psycho shot exitingville laboratories Scaling Portal.printlnisco designed dev kick Sahbirdhome conserv潜 अब nearly bilEndpoints Made What बहMAR,eM canc Missouri occasions.at Tara Picassoelling devilвер BaşScale episode prefabمر frenshared walking BASE torn vec UP turbo McDओnummerแม investig Photo agileDis JustSaveพบ thinly outpatientSur ldb imprint онParticipant sub strippedchoiceCoordinate obliv bom433 newspaper SqExam resized
```

Nhận xét: temperature càng thấp thì phản hồi ổn định và an toàn hơn; temperature càng cao thì phản hồi đa dạng hơn nhưng dễ lan man hoặc nhiễu, như kết quả temperature 1.5.

### Câu 1.2 — Chọn temperature cho sản phẩm
**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> Khoảng 0.2–0.4 cho chatbot hỗ trợ khách hàng vì câu trả lời phải nhất quán theo chính sách công ty/tổ chức, không bịa thông tin, mức này vẫn đủ lịch sự nhưng hạn chế các phản hồi quá khác nhau cho cùng một vấn đề.

### Câu 1.3 — Đánh đổi chi phí
Kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người gọi API 3 lần,
mỗi lần trung bình ~350 token đầu ra.

**Ước tính GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này? Nêu một
trường hợp GPT-4o xứng đáng với chi phí và một trường hợp nên dùng mini:**
> Mỗi ngày có 10.000 × 3 × 350 = 10.500.000 token đầu ra. Với giá output trong bảng, GPT-4o là 0.010 USD/1K token còn GPT-4o-mini là 0.0006 USD/1K token, nên GPT-4o đắt khoảng 16,7 lần; tương ứng khoảng 105 USD/ngày so với 6,3 USD/ngày nếu chỉ tính output. GPT-4o dùng cho task khó, cần suy luận tốt, chất lượng cao như tư vấn phân tích tài liệu phức tạp, mini phù hợp cho FAQ, phân loại, tóm tắt ngắn hoặc chatbot khối lượng lớn cần tối ưu chi phí.

---

## Block 2 — System Prompt & Token (trả lời sau Checkpoint 2)

### Câu 2.1 — Sức mạnh của persona
Gọi `chat_with_system_prompt` hai lần với cùng câu hỏi
**"Giải thích blockchain là gì?"** nhưng hai system prompt khác nhau:
- "Bạn là giáo viên tiểu học, giải thích thật đơn giản cho trẻ 8 tuổi."
- "Bạn là chuyên gia tài chính, trả lời chuyên sâu bằng thuật ngữ kỹ thuật."

**Hai phản hồi khác nhau như thế nào (độ dài, từ vựng, ví dụ)? System prompt
ảnh hưởng đến hành vi model ra sao?** (3–4 câu)
User prompt cho cả 2 lần: “Giải thích blockchain là gì?”

Model/API: NVIDIA NIM `meta/llama-3.1-8b-instruct` qua `OPENAI_BASE_URL=https://integrate.api.nvidia.com/v1`. Dùng mini model cho phần ghi nhận này vì worker của model 70B báo `ResourceExhausted` ở lần gọi persona thứ hai.

System prompt 1: “Bạn là giáo viên tiểu học, giải thích thật đơn giản cho trẻ 8 tuổi.”

Phản hồi :

```text
Chào các bạn nhỏ!

Hôm nay, chúng ta sẽ học về một khái niệm thú vị gọi là "Blockchain".

**Blockchain là gì?**

Blockchain là một loại sổ cái (hay cuốn sổ) đặc biệt. Sổ cái này không được giữ bởi một người hoặc một tổ chức nào, mà được lưu trữ trên nhiều máy tính khác nhau trên toàn thế giới.

**Làm thế nào nó hoạt động?**

Khi chúng ta muốn lưu trữ thông tin vào sổ cái, chúng ta sẽ tạo một "hợp đồng" (còn gọi là "block") và gửi nó đến các máy tính khác nhau trên toàn thế giới.

Sau đó, các máy tính này sẽ kiểm tra và xác minh thông tin trong "hợp đồng" đó. Nếu thông tin chính xác, thì "hợp đồng" đó sẽ được thêm vào sổ cái.

Và đây là điều đặc biệt: sau khi một "hợp đồng" đã được thêm vào sổ cái, thì nó sẽ không thể bị xóa hoặc thay đổi. Sổ cái sẽ luôn được cập nhật và phản ánh tất cả các "hợp đồng" đã được thêm vào.

**Tại sao blockchain lại quan trọng?**

Blockchain giúp chúng ta có thể:

* Lưu
```

System prompt 2: “Bạn là chuyên gia tài chính, trả lời chuyên sâu bằng thuật ngữ kỹ thuật.”

Phản hồi :

```text
Blockchain là một công nghệ dữ liệu phân tán (Decentralized Data) được sử dụng để lưu trữ và truyền tải thông tin một cách an toàn, minh bạch và không thể thay đổi. Công nghệ này dựa trên ý tưởng về một sổ cái (Ledger) phân tán, trong đó dữ liệu được lưu trữ và xác minh bởi một mạng lưới các nút (Node) phân tán trên toàn cầu.

Tính chất cơ bản của blockchain bao gồm:

1. **Phân tán**: Dữ liệu được lưu trữ và xác minh bởi một mạng lưới các nút phân tán, thay vì một nút trung tâm.
2. **Tự động hóa**: Mạng lưới blockchain tự động hóa quá trình xác minh và lưu trữ dữ liệu.
3. **Tính không thể thay đổi**: Dữ liệu được lưu trữ trên blockchain không thể thay đổi hoặc xóa sau khi đã được xác minh.
4. **Tính minh bạch**: Dữ liệu được lưu trữ trên blockchain có thể truy cập được bởi tất cả các nút trong mạng lưới.

Quá trình hoạt động của blockchain như sau:

1. **Xác minh**: Khi một nút trong mạng lưới thực hiện một giao dịch, nó sẽ được xác minh bởi các nút khác trong mạng lưới
```

Nhận xét: system prompt làm thay đổi rõ giọng văn, ví dụ, độ dài và mức độ thuật ngữ. Prompt giáo viên tiểu học dùng cách giải thích gần gũi hơn, còn prompt chuyên gia tài chính dùng nhiều khái niệm như dữ liệu phân tán, node, ledger và tính minh bạch.

### Câu 2.2 — tiktoken vs đếm từ
Chọn một đoạn văn tiếng Việt ~100 từ. So sánh số token theo `count_tokens`
(tiktoken) với ước lượng `số từ / 0.75` mà Part 1 đã dùng.

**Hai con số chênh nhau bao nhiêu phần trăm? Vì sao tiếng Việt thường tốn
nhiều token hơn tiếng Anh cùng độ dài?**
Text đầu vào dùng để đo token:

```text
Trong quá trình học lập trình AI, tôi nhận thấy việc đặt câu hỏi rõ ràng giúp mô hình trả lời chính xác hơn. Nếu prompt nêu bối cảnh, mục tiêu, định dạng mong muốn và giới hạn độ dài, phản hồi thường ít lan man và dễ sử dụng hơn. Ngược lại, prompt quá chung chung khiến mô hình phải tự suy đoán nhiều, nên kết quả có thể khác nhau giữa các lần gọi. Vì vậy, khi xây dựng ứng dụng thật, tôi cần thử nghiệm nhiều phiên bản prompt, đo chi phí token, kiểm tra lỗi và thu thập phản hồi người dùng trước khi triển khai rộng rãi.
```

Lệnh/hàm đã gọi: `count_tokens(text, model="gpt-4o")`.

Kết quả ghi nhận  từ lần đo: đoạn văn có 112 từ; `count_tokens` trả về 133 token; ước lượng `số từ / 0.75` là khoảng 149,3 token; chênh khoảng 10,9%.

Nhận xét: tiếng Việt có nhiều dấu, âm tiết tách bằng khoảng trắng và một số từ ghép gồm nhiều tiếng, nên tokenizer có thể chia nhỏ khác với cách ta đếm “từ”. Vì vậy đếm từ chỉ là ước lượng thô; khi tính chi phí thật nên dùng tokenizer.

---

## Block 3 — Streaming & Độ Bền (trả lời sau Checkpoint 3)

### Câu 3.1 — Trải nghiệm người dùng với streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì
non-streaming lại phù hợp hơn?** (1 đoạn văn)
> Streaming quan trọng nhất khi phản hồi dài hoặc người dùng đang chờ tương tác trực tiếp, ví dụ chatbot, trợ lý lập trình, tóm tắt tài liệu dài hoặc sinh nội dung nhiều đoạn. Việc thấy chữ xuất hiện dần giúp giảm cảm giác chờ và cho phép người dùng dừng sớm nếu câu trả lời không đúng hướng. Non-streaming phù hợp hơn khi cần xử lý kết quả như một khối hoàn chỉnh, ví dụ gọi API nền, phân loại dữ liệu, sinh JSON cần parse, hoặc tác vụ ngắn mà độ trễ không đáng kể. Khi đó code đơn giản hơn vì chỉ cần nhận một response hoàn chỉnh.

### Câu 3.2 — Vì sao backoff theo cấp số nhân?
**So với delay cố định (ví dụ luôn chờ 1 giây), exponential backoff có lợi
thế gì khi API bị quá tải? Điều gì xảy ra nếu hàng nghìn client cùng retry
với delay cố định giống nhau?**
> Exponential backoff giúp giảm áp lực lên API bằng cách chờ lâu hơn sau mỗi lần thất bại, cho hệ thống có thời gian hồi phục. Nếu luôn delay cố định 1 giây, hàng nghìn client có thể retry cùng lúc theo cùng nhịp, tạo “làn sóng” request mới và làm tình trạng quá tải kéo dài. Backoff theo cấp số nhân phân tán tải tốt hơn, đặc biệt nếu kết hợp thêm jitter ngẫu nhiên. Cách này cũng tiết kiệm tài nguyên client vì không thử lại quá dồn dập khi lỗi có khả năng là tạm thời.

---

## Block 4 — Mini-Project (trả lời sau Checkpoint 4)

### Câu 4.1 — Thiết kế persona
**Bạn chọn persona gì cho trợ lý của mình? Viết lại system prompt đó và giải
thích 1–2 lựa chọn từ ngữ quan trọng trong prompt (ví dụ: vì sao yêu cầu
"trả lời ngắn gọn", vì sao chỉ định ngôn ngữ...):**
> Persona: “You are a friendly teaching assistant for my AI ​​course, providing concise answers in English, explaining programming exercises step-by-step, and always offering small examples when needed.” Yêu cầu “trả lời ngắn gọn” để tránh phản hồi quá dài làm người học khó theo dõi trong CLI. Dùng tiếng Anh vì tiếng Việt tốn hơn gấp 2~3.5 số lượng token, đồng thời tiếng Anh giúp người học làm quen với thuật ngữ quốc tế. Cụm “step-by-step” vì người học cần hiểu lí do của mỗi bước.

### Câu 4.2 — Hạn chế & cải thiện
**Trợ lý của bạn hiện có hạn chế lớn nhất là gì (ví dụ: history chỉ 3 lượt,
không có bộ nhớ dài hạn, không kiểm duyệt nội dung...)? Đề xuất một cải
thiện cụ thể và mô tả ngắn cách triển khai:**
> Hạn chế lớn nhất là history chỉ giữ 3 lượt gần nhất nên trợ lý dễ quên thông tin quan trọng trong cuộc trò chuyện dài. Một cải thiện cụ thể là thêm cơ chế tóm tắt bộ nhớ: khi history vượt quá giới hạn, gọi model để tóm tắt các lượt cũ thành một message system hoặc assistant ngắn, rồi giữ summary đó cùng 3 lượt mới nhất. Cách này kiểm soát chi phí token nhưng vẫn duy trì ngữ cảnh dài hạn. Ngoài ra có thể lưu summary theo phiên vào file để người dùng tiếp tục sau khi đóng CLI.

---

## Danh Sách Kiểm Tra Nộp Bài

- [x] `python grade.py` — xem điểm tự động, mục tiêu ≥ 75/100
- [x] Cả 4 checkpoint pytest đều pass
- [x] Tất cả 9 câu trong file này đã được trả lời
- [ ] Đã copy bài làm vào folder `solution/` và zip theo hướng dẫn README
