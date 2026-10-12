# English Fluency Lab

一個以 Codex 為主要操作介面的個人英文練習與成長紀錄 repository。

目標是透過持續的情境對話、閱讀、寫作、複習與分析，提升日常生活、工作及旅遊所需的自然英文能力。所有教學原則、個人設定、對話證據與累積知識都保存在 Git 中，因此可以在不同電腦上延續同一套學習脈絡。

## 運作方式

Codex 從 repository 取得兩種核心資訊：

- [`AGENTS.md`](AGENTS.md)：每次操作都應遵守的教學、隱私、紀錄與評量原則。
- [`english-coach`](.agents/skills/english-coach/SKILL.md)：各種練習模式的執行流程、回饋格式與保存規則。

練習開始時，Codex 會讀取相關個人設定與既有學習知識。練習完成後，會保留原始回答與指導內容，並只把有證據支持的弱點或複習項目加入累積知識。

## 快速開始

### 已經有 repository 的電腦

在 Codex desktop app 或 IDE 中開啟 repository 資料夾，或使用 Codex CLI：

```shell
cd path/to/english-fluency-lab
codex
```

接著直接輸入：

```text
開始快速模式
```

如果想明確指定 skill，可以輸入：

```text
$english-coach 開始快速模式
```

### 在另一台電腦開始

先準備好 GitHub SSH 權限與 Codex，再執行：

```shell
git clone git@github.com:Brandon-HC-Wang/english-fluency-lab.git
cd english-fluency-lab
codex
```

也可以 clone 後直接使用 Codex desktop app 或 IDE 開啟該資料夾。

## 使用模式

| 模式 | 啟動範例 | 行為 |
| --- | --- | --- |
| 隨機模式 | `開始隨機模式` | 從日常、工作或旅遊挑選情境並持續對話 |
| 指定模式 | `開始指定模式：模擬在飯店反映房間太吵` | 使用指定角色、情境與語氣進行對話 |
| 快速模式 | `開始快速模式` | 兩到三次回覆後自動總結並保存紀錄 |
| 複習模式 | `開始複習模式` | 從複習佇列測試舊弱點；沒有紀錄時先做診斷 |
| 抽考模式 | `開始抽考模式` | 根據歷史錯誤與複習項目逐題抽考 |
| 分析模式 | `分析我目前的英文程度` | 根據既有證據產生程度與進度報告 |
| Baseline | `開始 baseline` | 建立初始對話、閱讀與寫作能力基準 |
| 寫作／改寫 | `幫我把這封工作訊息改成自然英文` | 改善自然度、結構與情境語氣 |
| 閱讀模式 | `開始閱讀模式` | 練習理解、推論、字義與摘要 |
| 弱點特訓 | `針對我常犯的時態錯誤進行特訓` | 集中練習一個已有證據的弱點 |

可以先開始快速模式或一般練習，再於之後執行 baseline；baseline 是建立初始能力基準的活動，不是開始練習的前提。一般短練習會保存對話證據與有依據的複習項目，不會僅憑幾次回覆直接更新程度評估。程度摘要通常在 baseline 或分析模式後更新，或在累積證據支持明顯變化時調整。

## 對話回饋

在互動式對話中，每次英文回覆後會依序收到：

1. `中文教練回饋`
   - 保留需要討論的原句
   - 提供自然英文版本
   - 以繁體中文說明一到三個重要觀念
2. `English reply`
   - 依照目前角色用英文自然回覆
   - 深入原本話題或開啟合理的下一步

回饋會區分真正的錯誤、不自然說法、語氣調整與純粹的可選替代，不會為了改寫而把正確句子說成錯誤。

一般對話持續到輸入：

```text
結束這次的聊天
```

快速模式則會在兩到三次回覆後自動結束。最後一回合仍會提供教練回饋，接著直接總結並保存紀錄，不再接續角色對話或提出下一個情境問題。

想練習時就開始，不設定固定的每週頻率或次數。一般對話沒有預設時間上限，由你手動結束後再總結並保存；快速模式維持兩到三次回覆後自動結束。也可以在開始時指定「今天只練五題」等當次長度；若指定時間預算，教練會縮小練習規模並安排收尾，不會突然截斷尚未完成的回答。

到期的複習項目會保留在佇列，等你下次練習時再使用。複習或抽考模式會優先挑選到期項目；一般對話則只在符合當次情境時適量帶入，不要求一次補完所有逾期項目。

複習預設採用 1、3、7、14 天的間隔，從實際練習日計算；答錯或需要提示時，隔一天再複習並重新累積。至少在三個不同日期、不同練習情境中連續獨立答對，且首尾相隔至少七天，才標記為熟練。首次熟練後隔 14 天確認，再答對則改為每 30 天維持複習。這是可調整的練習預設，不代表永久掌握。完整規則見 [review-policy.md](.agents/skills/english-coach/references/review-policy.md)。

## 學習資料

```text
english-fluency-lab/
├── AGENTS.md                       Codex 的 repository 原則
├── .agents/skills/english-coach/  英文教練工作流程
├── learner/                        個人偏好與學習目標
├── knowledge/                      累積程度、錯誤與複習佇列
├── sessions/                       每次完成的原始練習紀錄
├── assessments/                    Baseline 與分析報告
├── templates/                      Session 紀錄格式
└── evals/                          核心模式的驗收案例
```

`sessions/` 是原始學習證據；`knowledge/` 是根據證據整理、可持續修正的摘要。第一次完成相關活動時，Codex 會建立尚不存在的 `sessions/` 或 `assessments/` 年份目錄。

主要設定檔：

- [`learner/profile.md`](learner/profile.md)：語言、回饋與個人背景偏好
- [`learner/goals.md`](learner/goals.md)：長期目標與練習比例
- [`knowledge/current-level.md`](knowledge/current-level.md)：目前程度與評量信心
- [`knowledge/error-patterns.md`](knowledge/error-patterns.md)：有證據支持的重複錯誤
- [`knowledge/review-queue.md`](knowledge/review-queue.md)：等待間隔複習的項目
- [`knowledge/scenario-history.md`](knowledge/scenario-history.md)：已練習情境與分類

## 跨電腦同步

開始練習前先同步：

```shell
git pull --rebase
```

練習完成並確認紀錄沒有敏感資訊後，再提交與推送：

```shell
git status
git add -A
git diff --staged
git commit -m "Record English practice"
git push
```

Codex 不會自動 commit 或 push。為了降低衝突，避免同時在兩台電腦進行尚未同步的練習。

## 評量限制

- 文字對話只能直接觀察文字互動、閱讀與寫作，不能推估聽力。
- 少量對話中出現的詞彙不能代表完整單字量；分析會優先描述主動詞彙與用法範圍。
- CEFR 或 TOEIC 相關結果只作為有信心標示的估計，並會註明實際測量與未測量的能力。

## 隱私

建議將 repository 設為 private。不要在練習內容中保存密碼、API key、私人網址、客戶資料、公司機密或不必要的真實身分資訊。Git 會保留歷史版本，因此 commit 前應先檢查 staged diff。

## Codex 參考文件

- [Custom instructions with AGENTS.md](https://learn.chatgpt.com/docs/agent-configuration/agents-md)
- [Build skills](https://learn.chatgpt.com/docs/build-skills)
