# BITE | Slide architecture and speaker notes

Delivered presentation: **BITE.pptx**, 30 slides. The chapter structure follows the paper; the Abstract is combined with Introduction.

## Brief

- Audience: researchers with basic machine learning and computer vision knowledge.
- Purpose: explain the method and evidence for monocular 3D dog reconstruction.
- Language: English slides and architecture; Traditional Chinese speaker notes.
- Estimated presentation time: 25–35 minutes, depending on technical depth.
- Template: the previously selected 16:9 PowerPoint template; attribution on slide 29.
- Coverage: Introduction, Related Work, Approach, Experiments, Conclusion, then a standalone closing.

## Chapters

| Chapter | Slides | Count |
|---|---|---:|
|Introduction (including Abstract)|03–05|3|
|Related Work|06–07|2|
|Approach|08–17|10|
|Experiments|18–26|9|
|Conclusion and closing|27–30|4|

### P01 | cover | BITE

**Purpose:** BITE.

**Visible text**

BITE

Beyond Priors for Improved<br>
Three-D Dog Pose Estimation

Nadine Rüegg · Shashank Tripathi · Konrad Schindler<br>
Michael J. Black · Silvia Zuffi

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：這篇論文研究如何從單張犬隻影像重建三維形狀與姿態。報告會沿論文的主要章節，依序介紹研究動機、相關方法、BITE 的做法、實驗以及限制。

Source: Paper, p.1

</details>

### P02 | agenda | Outline

**Purpose:** Outline.

**Visible text**

Outline

01

Introduction

Problem and contributions

03–05

Related Work

Prior work and missing evidence

06–07

03

Approach

D-SMAL, contact and refinement

08–17

04

Experiments

Data, evaluation and ablations

18–26

05

Conclusion

Findings and limitations

27–30

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：目錄沿用論文的大章節。摘要與前言合併介紹，因兩者的主要動機與貢獻重疊。接著在方法章節拆解模型與接觸約束，再到實驗章節核對資料、評估與消融。

Source: Paper, pp.1–8

</details>

### P03 | section | Introduction

**Purpose:** Introduction.

**Visible text**

01

Introduction

Monocular 3D reconstruction<br>
and the limits of existing priors

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：先從問題設定開始：輸入只有一張照片，輸出是能呈現形狀與姿態的三維犬隻網格。這裡把摘要的貢獻概觀與前言合併，避免重複。

Source: Paper, §1, pp.1–2

</details>

### P04 | imageText | Why single-image 3D dog reconstruction is hard

**Purpose:** Why single-image 3D dog reconstruction is hard.

**Visible text**

Why single-image 3D dog reconstruction is hard

Depth ambiguity

Many 3D bodies can project to similar 2D evidence.

Self-occlusion

Sitting and lying hide limbs and deform the body.

Limited training priors

Available canine 3D pose data favors standing and walking.

Paper Figure 1: input images and estimated 3D dogs

**Figures / layout**

- Figure 1, p.1; paper figure cropped without distortion; layout box [500, 135, 405, 275] on 960 × 540 canvas.

<details>
<summary>Speaker notes and source</summary>

講稿：單張影像把深度投影掉，因此二維輪廓吻合不保證三維形狀正確。坐姿和臥姿還會遮住腿部，讓估計更困難。舊有姿態先驗的資料主要涵蓋站立與行走，容易把少見姿態拉回熟悉範圍。

Source: Paper, pp.1–2, Fig.1

</details>

### P05 | bullets | BITE: four contributions

**Purpose:** BITE: four contributions.

**Visible text**

BITE: four contributions

Dog-specific shape model

D-SMAL replaces a generic multi-species shape space.

Ground contact supervision

Contact and a local ground plane provide geometric evidence.

Refinement network

A coarse BARC+ prediction is refined beyond its pose prior.

3D evaluation

Rendered images of scanned dogs provide 3D reference geometry.

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：作者從四個方向處理問題：建立犬科專用的形狀空間、利用接觸資訊、設計可修正姿態的網路，以及建立可量測三維誤差的測試資料。這些貢獻互相配合，並非單純換一個姿態估計模型。

Source: Paper, §1, pp.1–2

</details>

### P06 | section | Related Work

**Purpose:** Related Work.

**Visible text**

02

Related Work

Model-based, model-free<br>
and contact-based reconstruction

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：相關工作主要分三類。模型式方法利用可動的形狀先驗；無模型方法有較大的表示彈性；接觸式方法則把人體和環境的互動加入推論。

Source: Paper, §2, pp.2–3

</details>

### P07 | bullets | Prior work and the gap BITE addresses

**Purpose:** Prior work and the gap BITE addresses.

**Visible text**

Prior work and the gap BITE addresses

Model-based: SMAL and BARC

Priors help ambiguity, but generic shape and narrow poses limit dogs.

Model-free reconstruction

Flexible surfaces often require video or additional assumptions.

Contact-based human models

Contact has improved human reconstruction; BITE adapts ground contact to dogs.

BITE keeps an articulated prior while adding contact evidence for refinement.

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：SMAL 是多物種四足動物模型，BARC 利用犬種資訊從影像估計犬隻。作者認為前者的形狀空間不夠針對犬隻，後者的姿態先驗仍受訓練姿態限制。BITE 沿用可動模型，增加地面接觸作為另一條幾何線索。

Source: Paper, §2, pp.2–3

</details>

### P08 | section | Approach

**Purpose:** Approach.

**Visible text**

03

Approach

D-SMAL, BARC+ refinement,<br>
contact losses and optional optimization

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：方法依論文分成 D-SMAL、BITE 網路、損失函數和測試時最佳化。先看形狀表示，再理解初始估計和修正階段如何合作。

Source: Paper, §3, pp.3–6

</details>

### P09 | imageText | D-SMAL: a dog-specific shape space

**Purpose:** D-SMAL: a dog-specific shape space.

**Visible text**

D-SMAL: a dog-specific shape space

Training shapes

39 scanned canine-family toy figurines: 5 prior + 34 new.

Registration and PCA

Register a common mesh and learn shape variations.

Additional controls

Variable limb lengths and ear articulation improve expressiveness.

Figure 2: mean shape and seven principal deformation modes

**Figures / layout**

- Figure 2, p.3; paper figure cropped without distortion; layout box [500, 135, 405, 275] on 960 × 540 canvas.

<details>
<summary>Speaker notes and source</summary>

講稿：D-SMAL 由三十九個犬科玩偶的掃描建立，其中五個來自原 SMAL，其餘三十四個新增。作者配準共同網格後學習形狀空間，並加入肢體長度調整；耳朵角度也在配準階段處理。玩偶掃描數不能誤認為真犬掃描數。

Source: Paper, §3.1, pp.3–4; Fig.2

</details>

### P10 | figure | BITE network overview

**Purpose:** BITE network overview.

**Visible text**

BITE network overview

Figure 3: BARC+ produces a coarse fit; BITE refines it using image and reprojection evidence.

Refinement predicts pose, camera, contact labels and ground flatness.

**Figures / layout**

- Figure 3, p.5; paper figure cropped without distortion; layout box [50, 155, 860, 275] on 960 × 540 canvas.

<details>
<summary>Speaker notes and source</summary>

講稿：這張原始架構圖從左往右讀。BARC 加上 D-SMAL 形成 BARC+，先得到姿態、形狀和影像空間的預測。接著重投影，將影像與二維線索送進修正網路；不同輸出頭預測修正後的姿態、相機、逐頂點接觸及地面平坦程度。

Source: Paper, §3.2, pp.4–5; Fig.3

</details>

### P11 | flow | BARC+: the coarse estimation stage

**Purpose:** BARC+: the coarse estimation stage.

**Visible text**

BARC+: the coarse estimation stage

Input

Single RGB<br>
image

2D evidence

Keypoints +<br>
silhouette

3D parameters

Shape, pose<br>
and camera

D-SMAL

Initial posed<br>
dog mesh

BARC+ retains BARC’s architecture while replacing SMAL with D-SMAL.

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：第一階段是 BARC 加上 D-SMAL，因此作者稱為 BARC+。網路先估計關鍵點和分割，再透過形狀、姿態分支以及相機參數形成初始網格。它仍使用原有姿態先驗，因此輸出可能偏向訓練資料中的常見姿態。

Source: Paper, §3.2–3.3, p.4

</details>

### P12 | bullets | Refinement uses 2D residual evidence

**Purpose:** Refinement uses 2D residual evidence.

**Visible text**

Refinement uses 2D residual evidence

Inputs

RGB image, BARC+ keypoints and silhouette, plus projections of the coarse mesh.

Operation

A 2D encoder and prediction heads estimate differential corrections.

Outputs

Refined pose, translation and camera; contact and flatness predictions.

Network refinement keeps the coarse shape fixed; shape refinement is tested separately.

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：修正階段同時接收初始網格投影和二維偵測結果，讓網路取得兩者之間的差異線索。它修正姿態與相機，另有接觸和地面平坦度輸出頭。這個階段不修正形狀參數；後面的消融會顯示原因。

Source: Paper, §3.2, p.4; Fig.3 p.5

</details>

### P13 | bullets | Ground-contact labels: training vs inference

**Purpose:** Ground-contact labels: training vs inference.

**Visible text**

Ground-contact labels: training vs inference

Training annotations

Annotators mark ground flatness and contact on paws or mesh vertices.

Training losses

For flat-ground examples, contact and penetration losses supervise geometry.

Inference predictions

The network predicts per-vertex contact and ground flatness.

Optional optimization

Predicted contact and flatness guide test-time fitting.

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：請區分訓練與推論。訓練時作者收集接觸及地面平坦度標註；測試時不需要人工接觸標註，改由網路預測。可選的測試時最佳化再利用這些預測，並只在判斷地面平坦時啟用接觸約束。

Source: Paper, §3.2–3.4 and §4.1, pp.4–6

</details>

### P14 | formula | Ground contact: fit a plane to contact points

**Purpose:** Ground contact: fit a plane to contact points.

**Visible text**

Ground contact: fit a plane to contact points

c = (1/m) Σᵢ pᵢ     A = [p₁ − c, …, pₘ − c]<br>
A = U Σ Vᵀ        Lplane = σ₃²

Input

m labeled contact points pᵢ on a uniformly remeshed surface.

Operation

Center points; the least-variance SVD direction defines the plane normal.

Output

Minimize squared contact-to-plane distances through σ₃².

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：對接觸頂點先計算中心 c，再將去中心化座標組成三乘 m 的矩陣 A。SVD 最小奇異值對應的左奇異向量是最佳平面法向量，最小平方距離之和為最小奇異值平方。使用均勻重網格可避免原模型的臉與腳掌頂點密度過高，主導損失。

Source: Paper, §3.3, pp.4–5, Eqs.1–3

</details>

### P15 | bullets | Ground penetration and other losses

**Purpose:** Ground penetration and other losses.

**Visible text**

Ground penetration and other losses

Penetration

Penalize non-contact vertices below the estimated ground plane.

Reprojection

Keypoint and silhouette losses maintain image alignment.

Auxiliary classification

Cross-entropy supervises vertex contact and ground flatness.

Joint regularizers

Discourage implausible limb torsion and sideways motion.

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：僅讓接觸點共平面仍可能讓其他部位穿過地面，所以另加穿透損失。二維關鍵點與輪廓損失維持影像一致性，接觸及平坦度用分類損失監督，再用關節規則避免不合理的扭轉和側向姿態。

Source: Paper, §3.3, p.5

</details>

### P16 | imageText | Beyond a restrictive pose prior

**Purpose:** Beyond a restrictive pose prior.

**Visible text**

Beyond a restrictive pose prior

Start from BARC+

A prior trained on simple poses produces a plausible initial fit.

Predict a correction

Scale the additive pose update by a constant factor of 0.1.

Allow unfamiliar poses

No hard bound prevents larger deviations after training.

Figure 6: input, BARC+ with contact, then BITE

**Figures / layout**

- Figure 6, p.8; paper figure cropped without distortion; layout box [500, 135, 405, 275] on 960 × 540 canvas.

<details>
<summary>Speaker notes and source</summary>

講稿：舊先驗提供穩定起點，卻可能限制坐姿與臥姿。BITE 不把先驗直接移除，而是在初始估計上預測差分修正；論文把修正乘上 0.1，以便訓練從小變化開始。這不是對最終修正量設置硬性上限。圖六展示接觸約束與修正網路的作用。

Source: Paper, §3.2–3.3, pp.4–5; Fig.6 p.8

</details>

### P17 | bullets | Optional test-time optimization

**Purpose:** Optional test-time optimization.

**Visible text**

Optional test-time optimization

Optimize per image

Update translation, focal length, pose and shape.

Two stages

First use PCA shape and limb parameters; then allow symmetric vertex shifts.

Losses and condition

Use predicted 2D cues; activate contact losses when ground is predicted flat.

Trade-off

Further 3D improvement costs extra runtime.

BITE-ttopt includes this optional optimization; BITE is the network output.

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：BITE-ttopt 在網路預測之後，對每張測試圖做迭代最佳化，因此與單次前向推論的 BITE 是不同設定。前半使用形狀與肢體參數，後半允許左右對稱的頂點位移。測試圖沒有人工二維標註，使用的是網路自己的二維預測。

Source: Paper, §3.4, pp.5–6

</details>

### P18 | section | Experiments

**Purpose:** Experiments.

**Visible text**

04

Experiments

Training data, 3D protocol,<br>
comparisons and ablation studies

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：現在依論文實驗章節說明訓練資料、三維測試協定、主要比較和消融。這樣才能判讀數值是來自真實照片、半合成測試，還是哪一個網路設定。

Source: Paper, §4, pp.6–8

</details>

### P19 | table | StanfordExtra contact annotations

**Purpose:** StanfordExtra contact annotations.

**Visible text**

StanfordExtra contact annotations

Batch sampling balances pose and ground-flatness groups; 2D labels and breed labels are also used.

|Training pose category|Images with contact labels|
|---|---|
|Standing or walking|2,554|
|Lying|795|
|Sitting|867|
|Other|89|
|Total|4,305|

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：作者在 StanfordExtra 的部分訓練影像補上接觸標註。四類加總為 4305 張，這不是整個 StanfordExtra 的總量。採樣器每批混合平坦與非平坦地面，並增加坐姿和臥姿，後續消融會顯示採樣器帶來的差異。

Source: Paper, §4.1, p.6; total calculated from reported counts

</details>

### P20 | imageText | 3D evaluation dataset and alignment

**Purpose:** 3D evaluation dataset and alignment.

**Visible text**

3D evaluation dataset and alignment

Semi-synthetic test set

26 textured scans of six dogs, rendered from seven views per dog.

Common inputs

Rendered 1080 × 1080 images with ground-truth bounding boxes.

Rigid alignment

Keypoint initialization, then scan-to-mesh alignment.

Figure 7: rendered scans used as test images

**Figures / layout**

- Figure 7, p.8; paper figure cropped without distortion; layout box [500, 135, 405, 275] on 960 × 540 canvas.

<details>
<summary>Speaker notes and source</summary>

講稿：測試資料由六隻真犬的二十六個帶紋理掃描組成，再渲染不同視角，形成半合成影像。所有網路都使用真值邊界框；評估前先依少量對應關鍵點初始化，再做包含旋轉、平移和尺度的剛性對齊。原文寫每隻犬七個視角，未在此推算測試影像總數。

Source: Paper, §4.2, pp.6–7; Fig.7 p.8

</details>

### P21 | metrics | Why evaluate both 3D distances?

**Purpose:** Why evaluate both 3D distances?.

**Visible text**

Why evaluate both 3D distances?

Scan → mesh

For each scan vertex, measure distance to the predicted surface.

A low score alone can miss extraneous predicted regions.

Mesh → scan

Measure predicted surface points against the scan.

Complements the first direction for deformable bodies.

Both errors are in centimeters after alignment; lower is better.

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：以二維 PCK 和輪廓 IoU 量測投影，深度方向的錯誤可能被掩蓋。三維評估則計算兩個方向的表面距離。掃描到預測網格不能充分懲罰多出來的預測表面，因此作者加入網格到掃描距離；兩者都在對齊後以公分報告。

Source: Paper, §4.2, pp.6–7

</details>

### P22 | table | BITE reduces 3D surface error

**Purpose:** BITE reduces 3D surface error.

**Visible text**

BITE reduces 3D surface error

Against BARC: BITE improves by 0.33 cm and 0.78 cm, respectively.

Semi-synthetic scan test; cm, lower is better. ttopt adds per-image optimization.

|Method|Scan → mesh ↓|Mesh → scan ↓|
|---|---|---|
|WLDO|2.65|7.55|
|CTF|2.59|6.17|
|BARC|2.40|3.93|
|BITE|2.07|3.15|
|BITE-ttopt|2.03|2.84|

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：表一是在半合成掃描測試集的三維比較。相對 BARC，BITE 的掃描到網格誤差由 2.40 降為 2.07 公分，網格到掃描由 3.93 降為 3.15。BITE-ttopt 進一步降到 2.03 和 2.84，但使用了額外的測試時最佳化，因此不能忽略運算成本。

Source: Paper, §4.3, Table 1, p.7; differences calculated from table

</details>

### P23 | figure | Qualitative comparison with prior methods

**Purpose:** Qualitative comparison with prior methods.

**Visible text**

Qualitative comparison with prior methods

Rows: WLDO, CTF, BARC, BITE and BITE-ttopt; columns show different test images.

Inspect the estimated 3D pose from the input view and a second view.

**Figures / layout**

- Figure 4, p.8; paper figure cropped without distortion; layout box [50, 155, 860, 275] on 960 × 540 canvas.

<details>
<summary>Speaker notes and source</summary>

講稿：圖四每一欄是不同輸入，每一列是不同方法。請同時看輸入影像視角和旁邊的另一個三維視角，因為只看原圖投影可能掩蓋深度錯誤。這些是定性範例，整體效能仍應以表一的雙向距離判斷。

Source: Paper, Fig.4, p.8

</details>

### P24 | table | Ablation: contact and refinement matter

**Purpose:** Ablation: contact and refinement matter.

**Visible text**

Ablation: contact and refinement matter

For BITE, adding contact lowers error by 0.23 cm and 1.01 cm.

Same semi-synthetic test and cm metrics; sampler is the pose-balanced training sampler.

|Configuration|Scan → mesh ↓|Mesh → scan ↓|
|---|---|---|
|BARC+ without contact|2.32|3.92|
|BARC+ with contact|2.13|3.48|
|BITE without contact|2.30|4.16|
|BITE without sampler|2.09|3.31|
|BITE|2.07|3.15|

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：消融表說明哪個元件有作用。BITE 移除接觸後，兩個誤差為 2.30 和 4.16；加入接觸後降至 2.07 和 3.15。拿掉採樣器則只有小幅退步。這些差值是絕對公分，不是相對百分比，也不能把所有改善歸因於單一元件。

Source: Paper, §4.4, Table 2, p.7; differences calculated from table

</details>

### P25 | imageText | Refinement helps poses outside the prior

**Purpose:** Refinement helps poses outside the prior.

**Visible text**

Refinement helps poses outside the prior

BARC+ with contact

A restrictive prior can still fit poses close to training examples.

BITE refinement

Adds flexibility for sitting and lying beyond the prior.

Interpretation

The examples illustrate behavior; Table 2 provides aggregate evidence.

Figure 6: top input; middle BARC+ with contact; bottom BITE

**Figures / layout**

- Figure 6, p.8; paper figure cropped without distortion; layout box [500, 135, 405, 275] on 960 × 540 canvas.

<details>
<summary>Speaker notes and source</summary>

講稿：圖六的三列依次是輸入、加入接觸的 BARC+，以及 BITE。某些姿態接近先驗時，初始模型已能處理；但偏離較大的姿態，需要修正網路的彈性。這是原文挑選的視覺案例，不宜將它當作單獨的整體成功率。

Source: Paper, §4.4, p.7; Fig.6 p.8

</details>

### P26 | table | Shape refinement can degrade 3D accuracy

**Purpose:** Shape refinement can degrade 3D accuracy.

**Visible text**

Shape refinement can degrade 3D accuracy

Changing shape during network refinement can satisfy contact by distorting anatomy.

The optional test-time optimization does allow shape changes; it is a distinct stage.

|Configuration|Scan → mesh ↓|Mesh → scan ↓|
|---|---|---|
|BITE: shape fixed in refinement|2.07|3.15|
|Allow shape updates in BARC+|2.12|3.17|
|Predict shape in refinement|2.29|4.24|

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：作者測試將形狀也放進修正網路，但表二顯示兩種做法都使三維誤差上升。可能的失敗例子是把腿縮短，來讓軀幹接近地面，而非修正姿態。要區分這裡的網路修正階段與另一個測試時最佳化；後者仍允許形狀改變。

Source: Paper, §4.4, Table 2, p.7

</details>

### P27 | section | Conclusion

**Purpose:** Conclusion.

**Visible text**

05

Conclusion

Contributions, limitations<br>
and next research questions

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：最後回到作者的結論，將已驗證的貢獻與尚未解決的問題分開。數值支持的是指定測試協定下的三維表面誤差改善，不代表所有情境均已解決。

Source: Paper, §5, pp.7–8

</details>

### P28 | bullets | Conclusions

**Purpose:** Conclusions.

**Visible text**

Conclusions

D-SMAL

A dog-specific parametric model improves the available shape representation.

Contact-guided refinement

Ground constraints help move beyond the narrow pose prior.

3D evidence

BITE and BITE-ttopt improve both reported surface-distance metrics.

A useful prior is a starting point; additional geometry can guide refinement.

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：主要結論有三點。D-SMAL 提供犬科專用形狀空間；接觸幾何提供先驗之外的線索；在作者的半合成掃描測試上，BITE 的雙向表面誤差均低於比較方法。這些結論都必須放在該資料集與對齊協定下理解。

Source: Paper, §5, pp.7–8; Tables 1–2, p.7

</details>

### P29 | bullets | Limitations and future directions

**Purpose:** Limitations and future directions.

**Visible text**

Limitations and future directions

Test-set scope

Six scanned dogs; rendered images and ground-truth boxes limit deployment realism.

Ground assumption

Contact optimization is enabled when the predicted ground is flat.

Shape and geometry

Symmetric shifts cannot capture asymmetry; self-intersections remain.

Future work

Expand the shape space and model pose-dependent deformation.

Reported 3D gains do not establish robustness across all breeds, scenes or poses.

Paper: Rüegg et al., BITE. https://bite.is.tue.mpg.de/<br>
Template: Slidesgo; icons and images: Flaticon / Freepik.

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：評估只涵蓋六隻掃描犬，影像是渲染產生且使用真值邊界框，所以不能直接推論野外所有犬種與場景的效能。地面假設由平坦度預測控制；對稱頂點位移也無法表達不對稱細節。作者提出的後續方向包括自交問題、更豐富的形狀空間和姿態相關變形。

Source: Paper, §3.4 and §5, pp.5–8

</details>

### P30 | thanks | Thank you

**Purpose:** Thank you.

**Visible text**

Thank you

**Figures / layout**

Editable text, table, or diagram using the selected template.

<details>
<summary>Speaker notes and source</summary>

講稿：謝謝各位聆聽。

Source: Closing slide

</details>

## Sources and figure provenance

Rüegg, N., Tripathi, S., Schindler, K., Black, M. J., & Zuffi, S. *BITE: Beyond Priors for Improved Three-D Dog Pose Estimation*. Supplied camera-ready paper; [project page](https://bite.is.tue.mpg.de/). Figures 1–4 and 6–7 are cropped from the supplied paper; page numbers refer to the supplied PDF.

Template attribution: Slidesgo, with icons / imagery credited to Flaticon and Freepik.

## Evidence notes

- The 3D test uses 26 scans of six dogs and ground-truth bounding boxes. Do not infer the number of rendered test images from ambiguous wording.
- Surface errors are in centimeters after alignment and the two directions are distinct.
- BITE-ttopt includes optional per-image test-time optimization; BITE is the network prediction.
- The 4,305 contact-labeled examples are the sum of four reported groups, not the full StanfordExtra dataset.
- Allowing shape changes in network refinement is distinct from allowing shape updates in test-time optimization.
