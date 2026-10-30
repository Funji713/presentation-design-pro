# SyDog-Video | Slide architecture and speaker notes

Delivered file: SyDog-Video.pptx. **31 slides**, including the cover and final thank-you slide.

## Brief

- Audience: academic audience familiar with basic machine learning.
- Purpose: explain synthetic dog-video data, temporal pose estimation, and transfer evidence.
- Language: English slides and architecture; Traditional Chinese speaker notes.
- Suggested duration: 25–35 minutes (planning assumption).
- Design: 16:9, the previously selected template, with editable text, tables and diagrams.
- Metrics: PDJ differences are percentage points; MPJPE is normalized by the ground-truth box diagonal.

## Chapter allocation

| Chapter | Slides | Count |
|---|---|---:|
|Overview|01–04|4|
|Data generation|05–11|7|
|Model and evaluation|12–16|5|
|Results and discussion|17–31|15|

### P01 | cover | SyDog-Video

**Type / chapter:** cover / Overview

**Purpose:** SyDog-Video.

**On-slide text**

SyDog-Video

Learning temporal dog pose from synthetic video

A Synthetic Dog Video Dataset<br>
for Temporal Pose Estimation

Moira Shooter · Charles Malleson · Adrian Hilton<br>
International Journal of Computer Vision, 132:1986–2002 (2024)

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：這篇研究的核心是資料，而不是提出全新的神經網路。作者希望利用能自動產生標註的合成影片，讓時序姿態模型在少量真實犬隻影片上仍能學習。本報告先說明資料與模型，再以已知、未知犬種的不同結果評估其價值。

Source and conditions: Source: Shooter et al. (2024), p.1

</details>

### P02 | agenda | Outline

**Type / chapter:** agenda / Overview

**Purpose:** Outline.

**On-slide text**

Outline

01

Research question

Why synthetic data for video pose estimation?

03–04

Data generation

SyDog-Video and Dogio-11

05–11

03

Model and experiments

Temporal input, transfer and metrics

12–16

04

Results and discussion

Results, ablations and limitations

17–31

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：報告分成四個部分。先建立問題和貢獻，再釐清兩個資料集的角色。接著介紹時間資訊如何進入模型，以及如何比較不同訓練方式。最後逐一檢視實驗，特別留意已知與未知犬種，以及不同指標之間的差異。

Source and conditions: Source: Shooter et al. (2024), overview

</details>

### P03 | textimage | Challenges in dog video pose estimation

**Type / chapter:** textimage / Overview

**Purpose:** Challenges in dog video pose estimation.

**On-slide text**

Challenges in dog video pose estimation

Frame-by-frame estimation

Occlusion and large motion can obscure joints.

Video annotation is costly

Breeds, shapes, coats and poses vary widely.

Research question

Can synthetic video help when real labels are scarce?

Synthetic test example | green: ground truth; blue: prediction

**Figures and layout**

- PDF p.8, Figure 3, second sample; cropped from the paper without distortion. Layout box [left, top, width, height] = [596, 144, 290, 290] on a 960×540 canvas.

<details>
<summary>Speaker notes and sources</summary>

講稿：請先注意右側奔跑姿態，單張影像不一定能清楚呈現每一條腿。前後幀可能提供線索，但訓練時序模型也需要連續且有標註的影片。研究中的公開資料缺口，是作者寫作時的背景判斷，不能直接當作今天的資料集現況。

Source and conditions: Source: Shooter et al. (2024), pp.1–2; Fig.3 p.8

</details>

### P04 | numbers | Main contributions

**Type / chapter:** numbers / Overview

**Purpose:** Main contributions.

**On-slide text**

Main contributions

500

synthetic videos

87,500

frames

33

2D keypoints

Dataset

Unity3D generates keypoints, boxes and masks.

Evaluation

Test synthetic pretraining, fine-tuning and temporal context.

The contribution is data and transfer evaluation using an existing LSTM Pose Machine.

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：這三個數字分別描述影片數、影格數和標註種類，不能混用。每段影片有175張影格，所以總計87500張。模型採用既有的LSTM Pose Machine；真正要評估的是合成影片作為預訓練資料，是否能改善少量真實資料的學習。

Source and conditions: Source: Shooter et al. (2024), pp.2, 4, 6

</details>

### P05 | divider | Data generation

**Type / chapter:** divider / Data generation

**Purpose:** Data generation.

**On-slide text**

02

Data generation

Create temporally coherent synthetic video<br>
and define real-world test sets

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：接下來先看資料如何產生，再看資料如何切分。這兩件事直接決定後續結果代表什麼：合成資料要有變化，但同一影片不能失去時間連續性；測試資料則要區分已知犬種和未見犬種。

Source and conditions: Source: Shooter et al. (2024), §3–4

</details>

### P06 | flow | SyDog-Video generation pipeline

**Type / chapter:** flow / Data generation

**Purpose:** SyDog-Video generation pipeline.

**On-slide text**

SyDog-Video generation pipeline

Dog assets

5 models; 10 textures<br>
Walk, run, jump, sit, lie

Scene

Environment, light, camera<br>
Once per video

Render

175 continuous frames<br>
Automatic labels

Samples

5 frames per sequence<br>
Keypoints, boxes, masks

Automatic labels scale to video and include coordinates for occluded joints.

Generation example: 17,500 frames in ~45 min, including disk writes (i7 + RTX 2070 Max-Q).

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：流程由犬隻資產和動畫開始，再設定相機與環境，最後渲染並取得標註。這裡的175是每段影片影格數，五幀是模型輸入序列的長度。論文的45分鐘指17500幀的生成示例，並非整個資料集的生成時間。

Source and conditions: Source: Shooter et al. (2024), pp.3–4, 6

</details>

### P07 | appearance | Dog appearance and motion

**Type / chapter:** appearance / Data generation

**Purpose:** Dog appearance and motion.

**On-slide text**

Dog appearance and motion

5 models, 10 textures each

Hand-painted textures and fur add visual variety.

AI4Animation motion

Seeded randomization drives the action sequences.

Realism remains limited

Some poses are unnatural; mesh fur loses physics.

**Figures and layout**

- PDF p.4, Figure 1; cropped from the paper without distortion. Layout box [left, top, width, height] = [51, 109, 858, 205] on a 960×540 canvas.
- PDF p.4, Figure 2; cropped from the paper without distortion. Layout box [left, top, width, height] = [53, 359, 310, 118] on a 960×540 canvas.

<details>
<summary>Speaker notes and sources</summary>

講稿：上方對照同一批模型加毛髮前後的外觀，下方展示手繪材質。這些設計增加了視覺多樣性，但不等於完全真實。作者指出，部分模型的比例不適合原動畫系統；毛髮為了支援標註工具轉成網格，也失去風、重力及碰撞等效果。

Source and conditions: Source: Shooter et al. (2024), pp.3–4; Figs.1–2

</details>

### P08 | randomization | Randomization at the video level

**Type / chapter:** randomization / Data generation

**Purpose:** Randomization at the video level.

**On-slide text**

Randomization at the video level

Change across videos

Dog model and texture

503 HDRI environments

Lighting, viewpoint and lens

Keep within one video

Motion changes over time

Frames retain temporal continuity

Avoid arbitrary frame-wise changes

Randomize at OnIterationStart, not at every OnUpdate.

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：影片合成與單張影像合成的重要差異，是隨機化的時間尺度。跨影片需要多樣性，同一影片則需要連續性。因此作者在每一個影片迭代開始時設定條件，再讓動畫逐幀推進。這個安排讓模型看到合理的連續姿態，而非彼此無關的圖片。

Source and conditions: Source: Shooter et al. (2024), p.4; Fig.11 p.14; Table 11 p.15

</details>

### P09 | table | 33 keypoints and label alignment

**Type / chapter:** table / Data generation

**Purpose:** 33 keypoints and label alignment.

**On-slide text**

33 keypoints and label alignment

Matching names alone is insufficient: keypoint indices must also align.

Bounding boxes and segmentation masks are also provided; experiments target 2D pose.

|Aspect|Synthetic|Real Dogio-11|
|---|---|---|
|Coordinates|Projected from 3D model|Manually annotated|
|Occluded / uncertain|Coordinates retained|Uncertain points marked invisible|
|Index order|Synthetic ordering|Mapped to synthetic ordering|
|Unmatched points|Head and hips|Index −1; marked invisible|

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：這一頁先解釋標註的語意。真實資料並非直接沿用合成資料的索引，所以作者建立映射。合成資料的Head與Hips在映射表中為負一，會設為不可見。更重要的是，合成資料能標出人眼看不到的關節，而真實資料的不確定點通常沒有座標，這也影響不同資料集的比較。

Source and conditions: Source: Shooter et al. (2024), p.3; Table 1 p.5

</details>

### P10 | table | SyDog-Video scale and split

**Type / chapter:** table / Data generation

**Purpose:** SyDog-Video scale and split.

**On-slide text**

SyDog-Video scale and split

Leave-one-dog-type-out evaluation rotates the held-out type and averages results.

|Level|Scale / setup|Purpose|
|---|---|---|
|Full dataset|500 videos × 175 = 87,500 frames|Continuous poses|
|Model input|T = 5; 17,500 sequences|Five frames per sample|
|Training|14,000 sequences; 4 dog types|Learn temporal pose|
|Test|3,500 sequences; 1 unseen type|Unseen backgrounds|

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：這裡用表格把影片、影格和序列分開。模型看到的是五幀序列，不是把87500當作獨立影片。合成測試同時留出犬型與背景，Table 4又輪流留出五個犬型評估。因此它測的是合成域內，對新形狀和背景的泛化。

Source and conditions: Source: Shooter et al. (2024), p.6; Tables 3–4 p.7

</details>

### P11 | table | Dogio-11: known and unknown tests

**Type / chapter:** table / Data generation

**Purpose:** Dogio-11: known and unknown tests.

**On-slide text**

Dogio-11: known and unknown tests

Known uses held-out clips from the same videos; unknown tests an unseen breed.

14 source videos, 25–30 fps, 5–6 s each. Table 2 reports 155 training sequences; text also says 115.

|Split|Video / breed condition|5-frame sequences|
|---|---|---|
|Training|50% of sequences from 11 videos, 7 breeds|155|
|Known test|Other sequences from the same 11 videos|155|
|Unknown test|3 other videos; 1 unseen breed|96|

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：Dogio-11的名稱容易讓人誤以為只有十一段影片，實際原始資料有十四段。十一段用於切出訓練及known測試，另外三段保留給未知犬種。因為known來自相同影片，它不能代表完全獨立的新影片測試。另外，表二寫155訓練序列，但正文多處寫115；此處依表二，保留這個可重現性疑義。

Source and conditions: Source: Shooter et al. (2024), pp.3, 5–6; Table 2

</details>

### P12 | divider | Model and evaluation

**Type / chapter:** divider / Model and evaluation

**Purpose:** Model and evaluation.

**On-slide text**

03

Model and evaluation

Understand five-frame inputs and metrics<br>
before comparing transfer strategies

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：資料準備好之後，接著釐清模型如何利用時間資訊，以及結果如何衡量。這篇研究採用同一類時序模型來比較不同訓練來源，所以下面要特別注意哪些條件相同，哪些條件仍然不同。

Source and conditions: Source: Shooter et al. (2024), §3.3–4.3

</details>

### P13 | model | Temporal context in LSTM Pose Machine

**Type / chapter:** model / Model and evaluation

**Purpose:** Temporal context in LSTM Pose Machine.

**On-slide text**

Temporal context in LSTM Pose Machine

Frame t−1

Image features

LSTM memory

Carry information

Frame t

Current image

Pose output

Keypoint positions

Single-frame evidence

The current image provides local evidence for each joint.

Temporal evidence

Earlier frames provide context during motion or occlusion.

T = 5 continuous frames. This is a simplified conceptual diagram.

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：這是概念示意，不是完整網路的逐層架構。LSTM Pose Machine把原本的多階段影像估計延伸為跨幀的遞迴模型，利用記憶傳遞資訊。當某一幀的關節線索較弱時，時間前後文可能有幫助。實際合成訓練使用五幀序列；後面會用NoTemp實驗檢查這個作用。

Source and conditions: Source: Shooter et al. (2024), pp.4–5

</details>

### P14 | metrics | Evaluation metrics: PDJ and MPJPE

**Type / chapter:** metrics / Model and evaluation

**Purpose:** Evaluation metrics: PDJ and MPJPE.

**On-slide text**

Evaluation metrics: PDJ and MPJPE

PDJ@0.1 ↑

Distance ≤ 0.1 × box diagonal

Percentage of correct keypoints

Higher is better; differences in points

Normalized MPJPE ↓

Mean Euclidean keypoint error

Normalized by box diagonal

Unitless; lower is better

PDJ counts correct keypoints; MPJPE measures average positional error.

Training: MSE loss; synthetic T = 5, batch size 2; Optuna used for real-data settings.

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：兩個指標回答不同問題。PDJ計算有多少關鍵點在容許距離內；MPJPE則看誤差的平均大小。因為PDJ有門檻，而平均誤差會受到較大錯誤影響，所以某個模型可能PDJ較高，MPJPE卻不是最低。後續不能只用其中一個指標宣稱全面最佳。

Source and conditions: Source: Shooter et al. (2024), pp.5–7

</details>

### P15 | strategies | Synthetic-to-real training strategies

**Type / chapter:** strategies / Model and evaluation

**Purpose:** Synthetic-to-real training strategies.

**On-slide text**

Synthetic-to-real training strategies

Real only

Dogio-11 → train

Failed to learn in this small-data setting

Synthetic only

SyDog-Video → real test

Measure direct cross-domain transfer

Pretrain, then tune

SyDog-Video → Dogio-11

Adapt using target-domain video

Mixed training

SyDog-Video + StanfordExtra

Combine synthetic and real examples

Fine-tuning and mixed training use different real datasets.

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：這四種策略是論文的基本實驗。不過，微調使用Dogio，而混合訓練使用StanfordExtra，真實資料來源並不相同。因此即使微調的表現較好，也不能將全部差異只歸因於先後順序。小型Dogio直接訓練失敗，是這篇設定下的觀察，不是所有小資料集的普遍定律。

Source and conditions: Source: Shooter et al. (2024), pp.5–8

</details>

### P16 | table | Pretraining sources and conditions

**Type / chapter:** table / Model and evaluation

**Purpose:** Pretraining sources and conditions.

**On-slide text**

Pretraining sources and conditions

Table 7 compares models after an additional Dogio-11 fine-tuning stage.

|Source|Data type|Key distinction|
|---|---|---|
|SyDog-Video|Synthetic video sequences|Automatic, complete keypoints|
|SyDog NoTemp|Repeated identical frames|Control without temporal change|
|StanfordExtra|~12k dog images|120 breeds; single images|
|Animal Pose|>4k multi-species images|Dogs, cats, horses, cows, sheep|
|APT-36K|3,774 derived sequences|Real data with temporal information|

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：先比較資料來源，才能理解後面的數字。StanfordExtra和Animal Pose是單張圖片，但APT-36K在這篇研究中被處理成序列，所以不能概括所有真實預訓練都沒有時間資訊。資料量、物種與標註完整度也不同。最直接的時間對照是SyDog與NoTemp。ImageNet預訓練在小型Dogio設定下也未成功學習。

Source and conditions: Source: Shooter et al. (2024), p.6; Table 7 p.9

</details>

### P17 | divider | Results and discussion

**Type / chapter:** divider / Results and discussion

**Purpose:** Results and discussion.

**On-slide text**

04

Results and discussion

Evaluate the domain gap and adaptation,<br>
then temporal value and generalization

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：接下來的結果由基本問題往外展開。先問合成資料訓練是否能直接用在真實影片，再問微調是否有效。之後檢查時間資訊、困難案例、二次微調及合成設計。每個結果都會保留測試集和指標條件。

Source and conditions: Source: Shooter et al. (2024), §5–6

</details>

### P18 | gap | Synthetic-only training leaves a domain gap

**Type / chapter:** gap / Results and discussion

**Purpose:** Synthetic-only training leaves a domain gap.

**On-slide text**

Synthetic-only training leaves a domain gap

Realism and randomization alone do not close the synthetic-to-real gap.

|Test condition|PDJ@0.1 ↑|MPJPE ↓|
|---|---|---|
|Synthetic: leave-one-type mean|77.40|0.15|
|Real Dogio: known|43.07|0.41|
|Real Dogio: unknown|37.36|0.58|

**Figures and layout**

- PDF p.8, Figure 3; cropped from the paper without distortion. Layout box [left, top, width, height] = [53, 313, 851, 136] on a 960×540 canvas.

<details>
<summary>Speaker notes and sources</summary>

講稿：合成留一犬型測試的平均PDJ有77.40，但直接測真實資料時降到43.07和37.36。這證明合成域學到的能力並未直接轉成真實域的可靠表現。這些是不同測試資料的結果，不把差距當作同一測試集上的提升幅度。也不要將這裡的合成平均和Table 7的own test混為相同協定。

Source and conditions: Source: Shooter et al. (2024), Tables 4–5 p.7; Fig.3 p.8

</details>

### P19 | table | Target fine-tuning mainly improves known dogs

**Type / chapter:** table / Results and discussion

**Purpose:** Target fine-tuning mainly improves known dogs.

**On-slide text**

Target fine-tuning mainly improves known dogs

Fine-tuning vs before: known +34.69; unknown +4.42 percentage points.

MPJPE (known / unknown): 0.41 / 0.58 before → 0.16 / 0.44 after.

|Strategy|PDJ known ↑|PDJ unknown ↑|
|---|---|---|
|Before fine-tuning|43.07|37.36|
|SyDog → Dogio fine-tuning|77.76|41.78|
|SyDog + StanfordExtra mixed|68.82|37.29|

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：這一頁先看紅色的微調列。Known提升34.69個百分點，Unknown只提升4.42，改善幅度很不對稱。這表示少量目標資料有效適應了已知條件，但對新犬種仍有限。混合訓練的PDJ較低，但要記得它使用StanfordExtra，並非控制相同真實資料的純訓練策略比較。

Source and conditions: Source: Shooter et al. (2024), Table 6 p.8

</details>

### P20 | fullimage | Pose predictions before and after fine-tuning

**Type / chapter:** fullimage / Results and discussion

**Purpose:** Pose predictions before and after fine-tuning.

**On-slide text**

Pose predictions before and after fine-tuning

Known Dogio-11 | top: before; bottom: after | green: truth; blue: prediction

Fine-tuning improves these examples, but does not solve unseen-breed generalization.

**Figures and layout**

- PDF p.9, Figure 4; cropped from the paper without distortion. Layout box [left, top, width, height] = [51, 148, 858, 311] on a 960×540 canvas.

<details>
<summary>Speaker notes and sources</summary>

講稿：請沿著同一欄比較上下兩張影像，綠色是真值，藍色是模型預測。作者用這組已知犬種範例展示微調後的位置改善。它能幫助理解數字代表的視覺效果，但不能取代整體評估；論文沒有以這張圖證明新犬種的泛化能力。

Source and conditions: Source: Shooter et al. (2024), Fig.4 p.9

</details>

### P21 | table | Pretraining: compare both PDJ and error

**Type / chapter:** table / Results and discussion

**Purpose:** Pretraining: compare both PDJ and error.

**On-slide text**

Pretraining: compare both PDJ and error

SyDog leads in PDJ; Animal Pose and APT achieve lower MPJPE in individual cases.

K = known; U = unknown. All models are fine-tuned on Dogio-11; datasets differ.

|Pretraining source|PDJ K ↑|PDJ U ↑|MPJPE K ↓|MPJPE U ↓|
|---|---|---|---|---|
|SyDog-Video|77.76|41.78|0.16|0.44|
|StanfordExtra|73.02|24.34|0.19|0.52|
|Animal Pose|74.03|25.99|0.15|0.51|
|APT-36K|60.84|27.04|0.29|0.30|

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：同樣用Dogio微調後，SyDog在這張表的Known和Unknown PDJ都最高。不過，Animal Pose的Known MPJPE是0.15，優於SyDog的0.16；APT的Unknown MPJPE也更低。因此合成預訓練有價值，但不能說它在每一種誤差指標都勝出，或把跨資料集差異完全歸因於時間資訊。

Source and conditions: Source: Shooter et al. (2024), Table 7 p.9

</details>

### P22 | table | Temporal control: SyDog vs NoTemp

**Type / chapter:** table / Results and discussion

**Purpose:** Temporal control: SyDog vs NoTemp.

**On-slide text**

Temporal control: SyDog vs NoTemp

The matched synthetic-data control supports a contribution from temporal context.

Both use LSTM Pose Machine and Dogio fine-tuning; MPJPE decreases by 0.07 in each split.

|Pretraining setup|PDJ known ↑|PDJ unknown ↑|
|---|---|---|
|NoTemp: repeated single frame|63.35|27.63|
|Temporal: consecutive frames|77.76|41.78|
|Temporal − NoTemp|+14.41|+14.15|

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：這是檢驗時間資訊最直接的對照。NoTemp保留相同網路，但每個階段輸入同一影像，因此移除了跨幀變化。連續影片在已知和未知犬種都提升約十四個PDJ百分點，兩個MPJPE也都下降0.07。結果支持時間資訊有用，仍不等於證明所有跨資料集的差異都只來自時間。

Source and conditions: Source: Shooter et al. (2024), p.6; Table 7 p.9

</details>

### P23 | table | Challenging cases: motion and occlusion

**Type / chapter:** table / Results and discussion

**Purpose:** Challenging cases: motion and occlusion.

**On-slide text**

Challenging cases: motion and occlusion

SyDog exceeds the strongest real-data comparator by 15.86 PDJ points.

Known challenging subset; Table 9 subset and overall values cannot be consistently reconciled.

|Pretraining source|Challenge PDJ ↑|Challenge MPJPE ↓|
|---|---|---|
|SyDog-Video|70.51|0.14|
|StanfordExtra|42.00|0.40|
|Animal Pose|47.39|0.31|
|APT-36K|54.65|0.20|

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：這一頁只比較原文Challenge欄，避免混合不同難度子集。SyDog的PDJ是70.51，較最佳真實對照APT高15.86個百分點，平均誤差也更低。不過，原表部分整體值無法由困難與簡單子集一致重建，所以這裡不推算整體加權結果，也不自行補充未交代的樣本構成。

Source and conditions: Source: Shooter et al. (2024), Table 9 p.12

</details>

### P24 | qualitative | Visual evidence across time

**Type / chapter:** qualitative / Results and discussion

**Purpose:** Visual evidence across time.

**On-slide text**

Visual evidence across time

Follow each row

Frames are sampled every 5 frames; inspect the leg and tail.

Compare sources

SyDog, StanfordExtra, Animal Pose and APT-36K.

Reading the figure

Green: truth; pink: prediction. All fine-tuned on Dogio.

Qualitative consistency;<br>
no jitter metric reported.

**Figures and layout**

- PDF p.10, Figure 5; cropped from the paper without distortion. Layout box [left, top, width, height] = [40, 128, 634, 359] on a 960×540 canvas.

<details>
<summary>Speaker notes and sources</summary>

講稿：先沿著最上方SyDog那一列由左到右看，再與下面不同預訓練來源比較。作者特別提到前腳與尾部的連續預測。這是定性證據，不能把視覺上較一致直接當成已量測的抖動改善百分比；論文沒有另列時間平滑度指標。大幅動作和遮蔽另有圖六與圖七。

Source and conditions: Source: Shooter et al. (2024), Fig.5 p.10; Figs.6–7 p.11

</details>

### P25 | table | Two-stage fine-tuning: a generalization trade-off

**Type / chapter:** table / Results and discussion

**Purpose:** Two-stage fine-tuning: a generalization trade-off.

**On-slide text**

Two-stage fine-tuning: a generalization trade-off

Animal Pose intermediate: unknown +16.94, but known −2.77 points.

Compared with direct Dogio fine-tuning; the single-stage result is best only for known PDJ here.

|After SyDog pretraining|PDJ known ↑|PDJ unknown ↑|
|---|---|---|
|Direct → Dogio|77.76|41.78|
|→ StanfordExtra → Dogio|59.75|47.18|
|→ Animal Pose → Dogio|74.99|58.72|
|→ APT-36K → Dogio|72.44|58.38|

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：這頁是理解泛化限制的重要補充。先經Animal Pose或APT，再以Dogio微調，未知犬種PDJ可提升到約58。以Animal Pose中繼為例，相對直接微調，Unknown提高16.94，而Known降低2.77。這表示最佳路徑取決於要優先改善哪個測試條件，不能照字面把單次微調稱為全面最佳。

Source and conditions: Source: Shooter et al. (2024), Tables 7–8 p.9

</details>

### P26 | background | More complex backgrounds do not always help

**Type / chapter:** background / Results and discussion

**Purpose:** More complex backgrounds do not always help.

**On-slide text**

More complex backgrounds do not always help

No ground plane performs best; people help known but reduce unknown PDJ.

|Synthetic background, fine-tuned|Known PDJ ↑|Unknown PDJ ↑|
|---|---|---|
|Original clean|77.76|41.78|
|No ground plane|79.94|48.00|
|People|79.24|38.90|
|Assets + people|74.14|39.76|

**Figures and layout**

- PDF p.12, Figure 8; cropped from the paper without distortion. Layout box [left, top, width, height] = [52, 112, 856, 138] on a 960×540 canvas.

<details>
<summary>Speaker notes and sources</summary>

講稿：上方是同一樣本在不同背景設定的樣子，左到右為clean、道具、人物、道具加人物。表格聚焦微調後的PDJ，無地面幾何版本在兩種測試集都較高。加入人物雖提升Known，卻降低Unknown，因此增加場景複雜度並不會自動帶來更好的泛化。

Source and conditions: Source: Shooter et al. (2024), Figs.8–9 p.12

</details>

### P27 | size | More synthetic data eventually plateaus

**Type / chapter:** size / Results and discussion

**Purpose:** More synthetic data eventually plateaus.

**On-slide text**

More synthetic data eventually plateaus

Around 7,700 sequences

Known plateaus; unknown may decline.

Small pretraining also helps

140 sequences yield ~73.42 known PDJ.

Experimental condition

No-ground-plane SyDog pretraining, then Dogio fine-tuning.

Distribution matching matters as well as the amount of data.

**Figures and layout**

- PDF p.13, Figure 10; cropped from the paper without distortion. Layout box [left, top, width, height] = [44, 141, 556, 319] on a 960×540 canvas.

<details>
<summary>Speaker notes and sources</summary>

講稿：先注意橫軸是對數尺度，而且樣本是一個五幀序列，不是單張影像。曲線顯示資料增加初期有效，但到了約7700序列，Known趨於飽和，Unknown還可能下降。這不是越多越差的普遍規律，而是這個合成分布與Dogio目標資料組合下的結果。

Source and conditions: Source: Shooter et al. (2024), Fig.10 p.13

</details>

### P28 | table | Appearance augmentation improves performance

**Type / chapter:** table / Results and discussion

**Purpose:** Appearance augmentation improves performance.

**On-slide text**

Appearance augmentation improves performance

Appearance vs none: known +5.04; unknown +7.33 percentage points.

No fur + full augmentation: known PDJ 80.53; other cells appear misplaced and are omitted.

|Synthetic augmentation|PDJ known ↑|PDJ unknown ↑|
|---|---|---|
|None|73.63|32.34|
|Appearance|78.67|39.67|
|Appearance + geometry|77.76|38.04|

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：外觀增強包括灰階、雜訊、亮度及對比等變化，能提升這組實驗的表現。再加入幾何增強並未進一步提高PDJ。作者也指出不加毛髮反而更好；但Table 10無毛髮那列的中間欄位疑似錯置，因此只引用欄位明確的Known PDJ 80.53，不自行修正整列。

Source and conditions: Source: Shooter et al. (2024), Table 10 p.13

</details>

### P29 | limitations | Limitations and interpretation

**Type / chapter:** limitations / Results and discussion

**Purpose:** Limitations and interpretation.

**On-slide text**

Limitations and interpretation

Generalization

Real-domain transfer is weak before fine-tuning; unseen breeds remain hard.

Representativeness

Five synthetic dog types; known clips come from the same videos.

Comparison conditions

Data scale, annotations and real-data sources differ.

Reproducibility

Training counts conflict; Tables 9–10 contain reported inconsistencies.

Useful pretraining evidence, but not proof of broad clinical or breed-level performance.

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：最後將限制分成四層：泛化、資料代表性、比較條件及報告一致性。這些限制不會抹去合成影片的價值，但會影響結論能推到多遠。這篇沒有驗證實際獸醫診斷效果，也沒有證明在廣泛犬種和環境皆可靠。未來擴充犬型、真實影片和獨立測試集，會是合理的研究延伸。

Source and conditions: Source: Shooter et al. (2024), pp.13–14; Tables 2, 6, 7, 9, 10

</details>

### P30 | closing | Conclusions and discussion

**Type / chapter:** closing / Results and discussion

**Purpose:** Conclusions and discussion.

**On-slide text**

Conclusions and discussion

Synthetic video supports pretraining

Automatic pose labels enable learning with limited real data.

A direct temporal control supports its value

NoTemp comparison: +14.41 known and +14.15 unknown PDJ points.

Adaptation and diversity remain important

The domain gap and unseen-breed challenges persist.

Shooter, M., Malleson, C., & Hilton, A. (2024).<br>
SyDog-Video: A Synthetic Dog Video Dataset for Temporal Pose Estimation.<br>
IJCV, 132, 1986–2002. doi:10.1007/s11263-023-01946-z

Figures cropped from paper (CC BY 4.0) · Template: Slidesgo<br>
Template icons and assets: Flaticon / Freepik

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：可以帶走三個重點。第一，合成影片確實能提供有用的預訓練。第二，NoTemp對照支持時間資訊的貢獻。第三，這項貢獻仍需要目標域適應，而且新犬種的泛化尚未完成。討論時可回到一個問題：若目標是陌生犬種，應優先增加合成外觀多樣性、真實影片，還是改變適應流程？這是研究延伸，不是本文已證明的答案。

Source and conditions: Source: Shooter et al. (2024), Tables 6–8; §6

</details>

### P31 | thanks | Thank you

**Type / chapter:** thanks / Results and discussion

**Purpose:** Thank you.

**On-slide text**

Thank you

**Figures and layout**

- Editable text, table or explanatory diagram, with template master elements.

<details>
<summary>Speaker notes and sources</summary>

講稿：謝謝各位聆聽。

Source and conditions: Closing slide; template credits appear on the preceding slide.

</details>

## Sources and assets

Shooter, M., Malleson, C., & Hilton, A. (2024). *SyDog-Video: A Synthetic Dog Video Dataset for Temporal Pose Estimation*. International Journal of Computer Vision, 132, 1986–2002. [DOI](https://doi.org/10.1007/s11263-023-01946-z); [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). Figures are cropped from the supplied paper. The original template credits Slidesgo, Flaticon and Freepik on slide 30.

## Source data notes

1. Table 2 reports 155 training sequences; the text also reports 115.
2. Table 9 subset and overall values cannot be consistently reconstructed; the deck compares the challenge column only.
3. Table 10 has apparently misplaced cells in the no-fur row; only known PDJ 80.53 is quoted. Its full-augmentation unknown value also differs from Tables 6–7.
4. Mixed training uses StanfordExtra; direct fine-tuning uses Dogio.
5. Two-stage fine-tuning improves unknown-breed PDJ with a known-breed trade-off.

