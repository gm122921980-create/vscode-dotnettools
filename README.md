{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "additionalProperties": false,
  「特性」： {
    "$schema": {
      描述：已忽略。可在某些編輯器中進行設定以取得程式碼補全、驗證和檔案。
      「例子」： [
        "https://openapi.vercel.sh/vercel.json"
      ],
      "type": "string"
    },
    「別名」：{
      "description": "部署狀態為“READY”並且目標環境為“生產”時將分配別名。客戶端需要向其 API 發送“GET”請求以確保分配成功。"
      「例子」： [
        "example.vercel.app"
      ],
      “oneOf”：[
        {
          “private”：true，
          "type": "string"
        },
        {
          "專案": {
            "maxLength": 253,
            "type": "string"
          },
          “maxItems”：50，
          "maxLength": 253,
          "類型": "陣列"
        }
      ]
    },
    「建造」： {
      "additionalProperties": false,
      “描述”：“包含另一個對象，其中包含要提交給當前過程的資訊的對象”，
      「已棄用」：是，
      「特性」： {
        "env": {
          "additionalProperties": false,
          "description": "包含配置環境變數名稱和值的對象，這些變數將提交給建構。可以在值前加上 `@` 來引用金鑰匙。"
          「例子」： {
            "A_SECRET": "@a-secret"
          },
          「已棄用」：是，
          「maxProperties」：1000，
          "minProperties": 0,
          "patternProperties": {
            ".+": {
              "maxLength": 65536,
              "minLength": 0,
              "type": "string"
            }
          },
          "type": "object"
        }
      },
      "type": "object"
    },
    "構建": {
      "description": "包含指向有效來源檔案的 src 引用的建構描述清單。"
      「已棄用」：是，
      "專案": {
        "additionalProperties": false,
        「特性」： {
          "config": {
            "description": "選擇性地，一個包含任意元資料的對象，要傳遞給當前器",
            "type": "object"
          },
          "src": {
            "description": "一個 glob 表達式或路徑名。如果解析出多個文件，則為每個匹配的文件創建一個構建。它可以包含 `*` 和 `**`。"
            "maxLength": 4096,
            "minLength": 1,
            "type": "string"
          },
          「使用」： {
            "description": "一個將在建置過程中安裝的 npm 模組。它可以包含一個語意化版本相包含的版本（例如：`@org/proj@1`）",
            "maxLength": 256,
            "minLength": 3,
            "type": "string"
          }
        },
        「簡單的」： [
          “使用”
        ],
        "type": "object"
      },
      “maxItems”：128，
      "minItems": 0,
      "類型": "陣列"
    },
    "cleanUrls": {
      "description": "設定為「true」時，所有 HTML 檔案和 Serverless Functions 的副檔名都會被移除。當存取以副檔名末尾的路徑時，系統會傳回 308 回應，將使用者端重新導向到商標副檔名的路徑。 "
      "type": "boolean"
    },
    "env": {
      "additionalProperties": false,
      "description": "包含配置環境變數名稱和值的物件。可以引用在值前加上 `@` 來金鑰。"
      「例子」： {
        "A_SECRET": "@a-secret"
      },
      「已棄用」：是，
      「maxProperties」：1000，
      "minProperties": 0,
      "patternProperties": {
        ".+": {
          "maxLength": 65536,
          "minLength": 0,
          "type": "string"
        }
      },
      "type": "object"
    },
    "passiveRegions": {
      "description": "部署的無伺服器函數應部署到被動區域的備份，在 Lambda 函數中斷期間可以將故障轉移到這些區域。"
      「例子」： [
        "iad1",
        "cle1"
      ],
      "專案": {
        "maxLength": 256,
        "type": "string"
      },
      “maxItems”：4，
      "minItems": 1,
      "類型": "陣列"
    },
    "functionFailoverRegions": {
      "description": "與passiveRegions相同。CPU區域陣列，用於部署指定的無伺服器功能部署到的區域，以便在Lambda函數發生故障時可以將故障轉移到這些區域。"
      「例子」： [
        "iad1",
        "cle1"
      ],
      "專案": {
        "maxLength": 256,
        "type": "string"
      },
      “maxItems”：4，
      "minItems": 1,
      "類型": "陣列"
    },
    "functions": {
      "additionalProperties": false,
      "description": "一個描述無伺服器函數自訂選項的物件。每個鍵都必須是與您要自訂的無伺服器函數的路徑一致的 glob 模式（例如 `api/*.js` 或 `api/test.js`）。"
      「例子」： {
        "src/pages/**": {
          “maxDuration”：6，
          「記憶體」：1024
        }
      },
      “maxProperties”：50，
      "minProperties": 1,
      "patternProperties": {
        "^.{1,256}$": {
          "additionalProperties": false,
          「特性」： {
            「排除檔案」：{
              "description": "用於匹配無伺服器函數中修復檔案的 glob 模式。如果您使用的是社群執行時，則行為可能會有所不同。"
              "maxLength": 256,
              "type": "string"
            },
            "includeFiles": {
              "description": "用於匹配應包含在 Serverless 函數中的文件中的 glob 模式。如果您使用的是社區運行時，則行為可能會有所不同。"
              "maxLength": 256,
              "type": "string"
            },
            "maxDuration": {
              "description": "您的無伺服器函數在每個請求中應運行多長時間（以秒為單位，循環 1 秒和您的套餐最大限制之間），或使用 "max" 以使用您的套餐允許的最多。"
              “oneOf”：[
                {
                  "type": "number",
                  「輕輕」：1，
                  「上」：1800
                },
                {
                  "type": "string",
                  「枚舉」：[
                    “最高”
                  ]
                }
              ]
            },
            「記憶」：{
              "description": "一個整數，用於定義應為您的無伺服器函數提供的記憶體大小（目前 128 和 10240 之間）。"
              「頂部」：10240，
              「最低」：128，
              "type": "number"
            },
            "運行時": {
              "description": "運行時的 npm 套件名稱，包括其版本",
              "maxLength": 256,
              "type": "string"
            },
            「區域」：{
              “描述”：“此無伺服器函數應部署到的區域資料庫。”
              "專案": {
                "maxLength": 256,
                "type": "string"
              },
              “maxItems”：1000，
              "minItems": 1,
              "類型": "陣列"
            },
            "functionFailoverRegions": {
              “描述”：“此無伺服器函數在 Lambda 函數中斷期間可以將故障轉移到被動區域資料庫。”
              "專案": {
                "maxLength": 256,
                "type": "string"
              },
              “maxItems”：4，
              "minItems": 0,
              "類型": "陣列"
            },
            "supportsCancellation": {
              "description": "一個布林值，用來定義函數是否支援取消操作（預設值：false）",
              "type": "boolean"
            },
            "experimentalTriggers": {
              描述：此無伺服器函數的一系列實驗性波形。目前僅支援隊列波形。
              "類型": "備份",
              “maxItems”：10，
              "專案": {
                “oneOf”：[
                  {
                    "type": "object",
                    「簡單的」： [
                      “類型”，
                      “話題”，
                      “消費者”
                    ],
                    "additionalProperties": false,
                    「特性」： {
                      “類型”： {
                        "描述": "此觸發器處理的事件類型模式",
                        "type": "string",
                        區別："queue/v1beta"
                      },
                      「話題」： {
                        "描述": "要消費的佇列主題的名稱",
                        "type": "string",
                        "minLength": 1,
                        「maxLength」：256
                      },
                      「消費者」： {
                        "描述": "此消費的消費者群名稱",
                        "type": "string",
                        "minLength": 1,
                        「maxLength」：256
                      },
                      "maxDeliveries": {
                        "描述": "最大投遞嘗試次數",
                        "type": "number",
                        「輕輕」：1，
                        「頂部」：64
                      },
                      "retryAfterSeconds": {
                        “描述”：“重試失敗執行前的延遲時間（秒）”
                        "type": "number",
                        「最低」：5，
                        「頂部」：86400
                      },
                      "initialDelaySeconds": {
                        “描述”：“首次執行嘗試前的初始延遲時間（秒）”
                        "type": "number",
                        「輕輕」：0，
                        「頂部」：86400
                      },
                      "maxConcurrency": {
                        "描述": "此消費者的最大同時執行次數",
                        "type": "number",
                        「輕輕」：1，
                        「頂部」：100
                      }
                    }
                  },
                  {
                    "type": "object",
                    「簡單的」： [
                      “類型”，
                      “話題”
                    ],
                    "additionalProperties": false,
                    「特性」： {
                      “類型”： {
                        "描述": "此觸發器處理的事件類型模式",
                        "type": "string",
                        區別："queue/v2beta"
                      },
                      「話題」： {
                        "描述": "要消費的佇列主題的名稱",
                        "type": "string",
                        "minLength": 1,
                        「maxLength」：256
                      },
                      "maxDeliveries": {
                        "描述": "最大投遞嘗試次數",
                        "type": "number",
                        「輕輕」：1，
                        「頂」：1048576
                      },
                      "retryAfterSeconds": {
                        “描述”：“重試失敗執行前的延遲時間（秒）”
                        "type": "number",
                        "exclusiveMinimum": 0,
                        「頂部」：86400
                      },
                      "initialDelaySeconds": {
                        “描述”：“首次執行嘗試前的初始延遲時間（秒）”
                        "type": "number",
                        「輕輕」：0，
                        「頂部」：86400
                      },
                      "maxConcurrency": {
                        "描述": "此消費者的最大同時執行次數",
                        "type": "number",
                        「輕輕」：1，
                        「頂」：16384
                      }
                    }
                  }
                ]
              }
            }
          },
          "type": "object"
        }
      },
      "type": "object"
    },
    "git": {
      "type": "object",
      「特性」： {
        "deploymentEnabled": {
          "description": "指定提交方案碼時不會觸發自動部署的分支。任何未指定的分支預設為“true”。"
          「例子」： {
            「主」：假
          },
          “oneOf”：[
            {
              "type": "boolean"
            },
            {
              "type": "object",
              "additionalProperties": {
                "type": "boolean"
              }
            }
          ]
        },
        「獨家性」：{
          “private”：true，
          "type": "object",
          "description": "如果指定，則 Git 倉庫將指定的團隊 ID 使用。未在清單中指定的團隊將無法連結新項目或建立新部署。"
          「特性」： {
            「團隊」：{
              "類型": "備份",
              描述：允許的團隊 ID 清單。
              "專案": {
                "type": "string"
              },
              “maxItems”：10，
              "minItems": 1
            }
          }
        }
      }
    },
    "github": {
      “private”：true，
      "type": "object",
      「特性」： {
        "autoAlias": {
          "description": "當設定為`false`時，無論安裝了是否安裝了GitHub應用程序，Vercel for GitHub都不會部署給定的專案。"
          "type": "boolean"
        },
        「自動取消作業」：{
          "description": "當設定為`false`時，Vercel for GitHub 將始終按順序建立個體，而取消不會最新的提交的構建。"
          "type": "boolean"
        },
        「啟用」：{
          "description": "如果設定為 false，Vercel for GitHub 將不會在合併時套用別名。"
          "type": "boolean"
        },
        「沉默的」： {
          「已棄用」：是，
          「描述」：[已棄用]請修改用控制面板中的專案設定：https://vercel.link/46vERTS 設定為「true」後，Vercel for GitHub 將停止對拉取要求和提交進行評論。
          "type": "boolean"
        }
      }
    },
    "headers": {
      "類型": "備份",
      “maxItems”：2048，
      描述：標頭定義清單。
      "專案": {
        "type": "object",
        "additionalProperties": false,
        「簡單的」： [
          “來源”，
          “標題”
        ],
        「特性」： {
          「來源」： {
            "description": "符合每個命名路徑名（不包括查詢字符串）的模式",
            "type": "string",
            “maxLength”：4096
          },
          "headers": {
            描述：一個包含對佇列的鍵值，表示每個回應頭。
            "類型": "備份",
            “maxItems”：1024，
            "專案": {
              "type": "object",
              "additionalProperties": false,
              「簡單的」： [
                “區域”，
                “價值”
              ],
              「特性」： {
                「大門」： {
                  "type": "string",
                  “maxLength”：4096
                },
                「價值」： {
                  "type": "string",
                  “maxLength”：32768
                }
              }
            }
          },
          「有」： {
            “描述”：“滿足所需的序列要求”，
            "類型": "備份",
            「maxItems」：16，
            "專案": {
              "anyOf": [
                {
                  "type": "object",
                  "additionalProperties": false,
                  「簡單的」： [
                    “類型”，
                    “價值”
                  ],
                  「特性」： {
                    “類型”： {
                      "描述": "要檢查的請求元素類型",
                      "type": "string",
                      「枚舉」：[
                        “主持人”
                      ]
                    },
                    「價值」： {
                      "description": "要符合的值。可以是字串（正規表示式）或條件操作物件。"
                      "anyOf": [
                        {
                          描述：用於匹配值的表示正規式。目標位置可以使用命名群體。
                          "type": "string",
                          “maxLength”：4096
                        },
                        {
                          "描述": "條件操作物件",
                          "type": "object",
                          "additionalProperties": false,
                          "minProperties": 1,
                          「特性」： {
                            "eq": {
                              描述：相等，
                              "anyOf": [
                                {
                                  "type": "string",
                                  “maxLength”：4096
                                },
                                {
                                  "type": "number"
                                }
                              ]
                            },
                            "neq": {
                              描述：不夠，
                              "type": "string",
                              “maxLength”：4096
                            },
                            "inc": {
                              "描述": "在陣列中",
                              "類型": "備份",
                              "專案": {
                                "type": "string",
                                “maxLength”：4096
                              }
                            },
                            "ninc": {
                              描述：不在資料庫中，
                              "類型": "備份",
                              "專案": {
                                "type": "string",
                                “maxLength”：4096
                              }
                            },
                            "pre": {
                              "描述": "以...開頭",
                              "type": "string",
                              “maxLength”：4096
                            },
                            "suf": {
                              "描述": "以...結尾",
                              "type": "string",
                              “maxLength”：4096
                            },
                            「關於」： {
                              "描述": "正規表示式",
                              "type": "string",
                              “maxLength”：4096
                            },
                            "gt": {
                              描述：大於，
                              "type": "number"
                            },
                            "gte": {
                              描述：大於或等於，
                              "type": "number"
                            },
                            "lt": {
                              "描述": "小於",
                              "type": "number"
                            },
                            "lte": {
                              “描述”：“小於或等於”，
                              "type": "number"
                            }
                          }
                        }
                      ]
                    }
                  }
                },
                {
                  "type": "object",
                  "additionalProperties": false,
                  「簡單的」： [
                    “類型”，
                    “區域”
                  ],
                  「特性」： {
                    “類型”： {
                      "描述": "要檢查的請求元素類型",
                      "type": "string",
                      「枚舉」：[
                        “標題”，
                        “餅乾”，
                        “詢問”
                      ]
                    },
                    「大門」： {
                      "description": "特定型別中包含的元素的名稱",
                      "type": "string",
                      “maxLength”：4096
                    },
                    「價值」： {
                      "description": "要符合的值。可以是字串（正規表示式）或條件操作物件。"
                      "anyOf": [
                        {
                          描述：用於匹配值的表示正規式。目標位置可以使用命名群體。
                          "type": "string",
                          “maxLength”：4096
                        },
                        {
                          "描述": "條件操作物件",
                          "type": "object",
                          "additionalProperties": false,
                          "minProperties": 1,
                          「特性」： {
                            "eq": {
                              描述：相等，
                              "anyOf": [
                                {
                                  "type": "string",
                                  “maxLength”：4096
                                },
                                {
                                  "type": "number"
                                }
                              ]
                            },
                            "neq": {
                              描述：不夠，
                              "type": "string",
                              “maxLength”：4096
                            },
                            "inc": {
                              "描述": "在陣列中",
                              "類型": "備份",
                              "專案": {
                                "type": "string",
                                “maxLength”：4096
                              }
                            },
                            "ninc": {
                              描述：不在資料庫中，
                              "類型": "備份",
                              "專案": {
                                "type": "string",
                                “maxLength”：4096
                              }
                            },
                            "pre": {
                              "描述": "以...開頭",
                              "type": "string",
                              “maxLength”：4096
                            },
                            "suf": {
                              "描述": "以...結尾",
                              "type": "string",
                              “maxLength”：4096
                            },
                            「關於」： {
                              "描述": "正規表示式",
                              "type": "string",
                              “maxLength”：4096
                            },
                            "gt": {
                              描述：大於，
                              "type": "number"
                            },
                            "gte": {
                              描述：大於或等於，
                              "type": "number"
                            },
                            "lt": {
                              "描述": "小於",
                              "type": "number"
                            },
                            "lte": {
                              “描述”：“小於或等於”，
                              "type": "number"
                            }
                          }
                        }
                      ]
                    }
                  }
                }
              ]
            }
          },
          「遺失的」： {
            “描述”：“滿足所需的序列要求”，
            "類型": "備份",
            「maxItems」：16，
            "專案": {
              "afrom fastapi import FastAPI
 
app = FastAPI()
 
@app.get("/")
def home():
    return {"message": "Hello from Python on Vercel"}
 
@app.get("/api/items/{item_id}")
def read_item(item_id: int):
    return {"item_id": item_id}[project]
name = "my-python-api"
version = "0.1.0"
requires-python = ">=3.12"
dependencies = [
    "fastapi>=0.117.1",
]{
  "$schema": "https://openapi.vercel.sh/vercel.json",
  "functions": {
    "api/**/*.py": {
      "excludeFiles": "{tests/**,__tests__/**,**/*.test.py,**/test_*.py,fixtures/**,__fixtures__/**,testdata/**,sample-data/**,static/**,assets/**}"
    }
  }
}

# 使用 GitHub Copilot 在 IDE 中获取代码建议
"files.associations": {
    "*.php4": "php",
    "*.php5": "php"
}
# 在环境中配置 GitHub Copilot

可以在受支持的 IDE 中启用、配置或禁用 GitHub Copilot。

<div class="ghd-tool jetbrains">

## 关于 JetBrains IDE 中的 GitHub Copilot

如果使用 JetBrains IDE，GitHub Copilot 可帮助你完成各种任务，包括生成代码建议、解释编辑器中的代码工作原理以及提供代码修复建议。 安装后，您可以启用或禁用 GitHub Copilot，而且可以在 IDE 或 GitHub 上配置高级设置。 本文介绍如何在 IntelliJ IDE 中配置 GitHub Copilot，但其他 JetBrains IDE 的用户界面可能有所不同。

## Prerequisites

要在 JetBrains IDE 中配置 GitHub Copilot，必须先安装 GitHub Copilot 插件。 有关详细信息，请参阅 [在环境中安装 GitHub Copilot 扩展](/zh/copilot/managing-copilot/configure-personal-settings/installing-the-github-copilot-extension-in-your-environment?tool=jetbrains)。

## 启用或禁用 GitHub Copilot

可从 JetBrains IDE 启用或禁用 GitHub Copilot。 JetBrains 窗口底部面板中的 GitHub Copilot 状态图标指示 GitHub Copilot 是启用还是禁用。 启用后，将突出显示图标。 禁用后，图标灰显。

1. 要启用或禁用 GitHub Copilot，请单击 JetBrains 窗口右侧底部面板中的状态图标。

   ![JetBrains IDE 中底部面板的屏幕截图。 GitHub Copilot 状态图标用深橙色框标出。](/assets/images/help/copilot/status-icon-jetbrains.png)

2. 如果要禁用 GitHub Copilot，系统会询问是全局禁用它，还是要禁用当前正在编辑的文件的语言。 要全局禁用，请单击“禁用完成”\*\*\*\*。 或者，单击特定于语言的按钮，为指定语言禁用 GitHub Copilot。

   ![全局或在 JetBrains IDE 中为当前语言禁用 GitHub Copilot 的菜单的屏幕截图。](/assets/images/help/copilot/disable-copilot-global-or-language-jetbrains.png)

## 重新绑定键盘快捷方式

使用 GitHub Copilot 时，可以在 JetBrains IDE 中使用默认键盘快捷方式获取内联建议。 有关默认键盘快捷方式的列表，请参阅 [IDE 中GitHub Copilot 的键盘快捷方式](/zh/copilot/reference/keyboard-shortcuts-for-github-copilot-in-the-ide)。

或者，可以将快捷方式重新绑定到每个特定命令的首选键盘快捷方式。 有关在 JetBrains IDE 中重新绑定键盘快捷方式的详细信息，请参阅 JetBrains 文档。 例如，可以查看 [IntelliJ IDEA](https://www.jetbrains.com/help/idea/mastering-keyboard-shortcuts.html#choose-keymap) 文档。

## 配置 GitHub Copilot 的高级设置

可以在 JetBrains IDE 中管理 GitHub Copilot 的高级设置，例如，配置 IDE 如何展示内联建议，以及选择启用或禁用 GitHub Copilot 的编程语言。

1. 在 JetBrains IDE 中，单击“文件”\*\*\*\* 菜单 (Windows) 或菜单栏中的应用程序名称 (macOS)，然后单击“设置”\*\*\*\*。1. 在左侧栏中，单击 **工具**，单击 **GitHub Copilot**，并查看 **常规设置** 和 **代码补全** 设置。
2. 根据个人首选项编辑设置。
   * 要调整代码建议的行为和外观，以及是否自动检查更新，请选中或取消选中相应的复选框。
   * 如果已选择接收自动更新，可以选择是接收稳定但频率较低的更新，还是接收可能不太稳定的夜间更新。 单击“更新通道”\*\*\*\* 下拉菜单，选择“稳定版”\*\*\*\* 以获取稳定更新，或选择“夜间版”\*\*\*\* 以获取夜间更新。

## 配置 GitHub Copilot 的语言设置

可以在 IDE 中或通过编辑 `github-copilot.xml` 文件来指定要激活或停用 GitHub Copilot 的语言。 如果在 IDE 中更改语言设置，可以单独选择和取消选择要激活或停用的语言。

如果更改 `github-copilot.xml` 文件中的语言设置，则可以指定单个语言，也可以使用通配符为所有语言激活或停用 GitHub Copilot 。 还可以指定例外，用以替代指定语言的通配符设置。 例如，可以为 Python 和 YAML 以外的所有语言停用 GitHub Copilot。 在安装 GitHub Copilot 扩展时，默认为所有语言激活 GitHub Copilot。

### 在 IDE 中配置语言设置

1. 在 JetBrains IDE 中，单击“文件”\*\*\*\* 菜单 (Windows) 或菜单栏中的应用程序名称 (macOS)，然后单击“设置”\*\*\*\*。1. 在左侧栏中，单击 **工具**，单击 **GitHub Copilot**，然后单击“ **完成**”。
2. 在“语言”下，选择或取消选择要激活或停用 GitHub Copilot 的语言的复选框。
3. 单击“应用”****，然后单击“确定”****。
4. 重启 JetBrains IDE 让更改生效。

### 编辑 `github-copilot.xml` 文件

若要在 `github-copilot.xml` 文件中配置语言设置，必须编辑 `languageAllowList`。 添加到 `languageAllowList` 的每一行都必须包含一个条目键和一个值。 条目键表示语言名称，(`*`) 表示通配符。 该值为 `true` 或 `false`。 如果值为 `true`，则激活指定语言的 GitHub Copilot。 如果值为 `false`，则停用指定语言的 GitHub Copilot。

文件所处目录如下所示：

* **macOS：**`~/Library/Application Support/JetBrains/<product><version>/options/github-copilot.xml`
* **Windows：**`%APPDATA%\JetBrains\<product><version>\options\github-copilot.xml`
* **Linux：**`~/.config/JetBrains/<product><version>/options/github-copilot.xml`

例如，如果在 macOS 上使用 IntelliJ IDEA 2021.1，该文件位于 `~/Library/Application Support/JetBrains/IdeaIC2021.1/options/github-copilot.xml`。

在 IDE 设置中更改默认语言配置之前，可能不会生成 `github-copilot.xml` 文件。 如果找不到该文件，则应尝试在 IDE 中修改默认语言设置。 有关更多信息，请参阅[在 IDE 中配置语言设置](#configuring-language-settings-in-the-ide)。

另外，可以手动创建文件，并将文件保存在上述操作系统的相应位置。 有关更多信息，请参阅[示例语言配置](#example-language-configurations)。

1. 在文本编辑器中打开 `github-copilot.xml` 文件。

2. 在 `<map>` 标记之间，为要激活或停用 GitHub Copilot 的语言添加行。 例如，为所有语言停用 GitHub Copilot：

   ```xml copy
   <entry key="*" value="false" />
   ```

3. 保存对 `github-copilot.xml` 文件的更改。

4. 重启 JetBrains IDE 让更改生效。

### 语言配置示例

默认的 `github-copilot.xml` 文件配置如下所示：此配置为所有语言启用 GitHub Copilot。

```xml copy
<application>
  <component name="github-copilot">
    <languageAllowList>
      <map>
        <entry key="*" value="true" />
      </map>
    </languageAllowList>
  </component>
</application>
```

要停用所有语言的 GitHub Copilot，将通配符 (`*`) 值更改为 `false`：

```xml copy
<application>
  <component name="github-copilot">
    <languageAllowList>
      <map>
        <entry key="*" value="false" />
      </map>
    </languageAllowList>
  </component>
</application>
```

要单独指定语言，则为要激活或停用 GitHub Copilot 的每种语言添加一个条目。 特定语言设置将覆盖通配符。 例如，要为 Python 和 YAML 激活 GitHub Copilot，并为其余语言停用 GitHub Copilot，请添加以下条目：

```xml copy
<application>
  <component name="github-copilot">
    <languageAllowList>
      <map>
        <entry key="*" value="false" />
        <entry key="Python" value="true" />
        <entry key="YAML" value="true" />
      </map>
    </languageAllowList>
  </component>
</application>
```

还可以添加配置，让 `languageAllowList` 在 IDE 的设置中变为只读。 此举可阻止更改 IDE 中的语言设置。 例如：

```xml copy
<application>
  <component name="github-copilot">
    <option name="languageAllowListReadOnly" value="true" />
    <languageAllowList>
      <map>
        <entry key="*" value="true" />
      </map>
    </languageAllowList>
  </component>
</application>
```

## 在 Copilot 上配置 GitHub.com 设置

如果您使用的是 Copilot Pro、Copilot Pro+ 或 Copilot Max 计划，则可以选择允许或禁止与公开可用代码匹配的内联建议。
你还可以允许或阻止收集和保留你输入的提示以及 Copilot 提供的建议。 可在个人设置 GitHub.com中配置此设置。 请参阅“[以个人订阅者身份管理 GitHub Copilot 策略](/zh/copilot/configuring-github-copilot/configuring-your-personal-github-copilot-settings-on-githubcom)”。

## 在 GHE.com 上对账户进行身份验证

如果在 Copilot 上使用 托管用户帐户 的 GHE.com 计划，则需要在登录之前更新一些设置。 请参阅 [在 GHE.com 上将 GitHub Copilot 与帐户配合使用](/zh/copilot/managing-copilot/configure-personal-settings/using-github-copilot-with-an-account-on-ghecom)。

## 其他阅读材料

* [GitHub Copilot 常见问题解答](https://github.com/features/copilot/#faq)

</div>

<div class="ghd-tool visualstudio">

## 关于 Visual Studio 中的 GitHub Copilot

如果使用 Visual Studio，GitHub Copilot 可帮助你完成各种任务，包括生成代码建议、解释编辑器中的代码工作原理以及提供代码修复建议。 安装后，您可以启用或禁用 GitHub Copilot，还可以在 Visual Studio 或 GitHub 上配置高级设置。

## Prerequisites

要在 Visual Studio 中配置 GitHub Copilot，必须安装 GitHub Copilot 插件。 有关详细信息，请参阅 [在环境中安装 GitHub Copilot 扩展](/zh/copilot/configuring-github-copilot/installing-the-github-copilot-extension-in-your-environment?tool=visualstudio)。

## 重新绑定键盘快捷方式

使用 GitHub Copilot 时，可使用 Visual Studio 中的内联建议的默认键盘快捷方式。 有关默认键盘快捷方式的列表，请参阅 [IDE 中GitHub Copilot 的键盘快捷方式](/zh/copilot/reference/keyboard-shortcuts-for-github-copilot-in-the-ide)。

如果不想在使用 GitHub Copilot 时使用 Visual Studio 中的默认键盘快捷方式，可使用每个特定命令的首选键盘快捷方式在键盘编辑器中重新绑定快捷方式。

1. 在 Visual Studio 菜单栏中，单击“工具”\*\*\*\* 下的“选项”\*\*\*\*。

   ![Visual Studio 菜单栏的屏幕截图。 “工具”菜单已展开，“选项”项以橙色边框突出显示。](/assets/images/help/copilot/vs-toolbar-options.png)

2. 在“选项”对话框中，单击“环境”\*\*\*\* 下的“键盘”\*\*\*\*。

3. 在“显示命令包含:”下，搜索要重新绑定的命令。

   ![“显示命令包含”搜索栏的屏幕截图。 在搜索字段中输入字符串“tools.next”。](/assets/images/help/copilot/vs-show-commands-containing.png)

4. 在“按快捷键”下，输入要分配给该命令的快捷键，然后单击“分配”\*\*\*\*。

   ![用于输入新键盘快捷方式分配的字段的屏幕截图。](/assets/images/help/copilot/vs-rebind-shortcut.png)

## 启用或禁用 GitHub Copilot

GitHub Copilot 窗口底部面板中的 Visual Studio 状态图标指示 GitHub Copilot 启用还是禁用。 启用后，图标的背景色将与状态栏颜色相匹配。 禁用后，将有一条对角线穿过它。

1. 若要启用或禁用 GitHub Copilot，请单击 GitHub Copilot 窗口底部面板中的 Visual Studio 图标。

   ![Visual Studio 中编辑器边距的屏幕截图，其中突出显示 GitHub Copilot 图标。](/assets/images/help/copilot/editor-margin-visual-studio.png)

2. 如果要禁用 GitHub Copilot，系统会询问是全局禁用建议，还是要禁用当前正在编辑的文件的语言。

   * 若要全局禁用 GitHub Copilot 的建议，请单击“全局启用”。
   * 若要禁用指定语言的 GitHub Copilot 的建议，请单击“对 LANGUAGE 启用”。

## 为 GitHub Copilot 配置 ReSharper

如果使用 ReSharper，当你将 ReSharper 配置为使用 GitHub Copilot 的本机 IntelliSense 时，GitHub Copilot 可能效果最佳。 有关 ReSharper 的详细信息，请参阅 [ReSharper 文档](https://www.jetbrains.com/resharper/documentation/documentation.html)

1. 在 Visual Studio 菜单栏的“扩展”\*\*\*\* 下，单击“扩展”****，然后单击“管理扩展”****。
2. 在“选项”对话框中，单击“环境”\*\*\*\* 下的“IntelliSense”****，然后单击“常规”****。
3. 在“常规”下选择 **Visual Studio**，然后单击“保存”\*\*\*\*。

## 在 Copilot 上配置 GitHub.com 设置

如果您使用的是 Copilot Pro、Copilot Pro+ 或 Copilot Max 计划，则可以选择允许或禁止与公开可用代码匹配的内联建议。
你还可以允许或阻止收集和保留你输入的提示以及 Copilot 提供的建议。 可在个人设置 GitHub.com中配置此设置。 请参阅“[以个人订阅者身份管理 GitHub Copilot 策略](/zh/copilot/configuring-github-copilot/configuring-your-personal-github-copilot-settings-on-githubcom)”。

## 在 GHE.com 上对账户进行身份验证

如果在 Copilot 上使用 托管用户帐户 的 GHE.com 计划，则需要在登录之前更新一些设置。 请参阅 [在 GHE.com 上将 GitHub Copilot 与帐户配合使用](/zh/copilot/managing-copilot/configure-personal-settings/using-github-copilot-with-an-account-on-ghecom)。

## 启用 接下来的编辑建议

要在 Visual Studio 中使用 接下来的编辑建议，需先启用该功能。

1. 在 Visual Studio 菜单栏中，单击“工具”\*\*\*\* 下的“选项”\*\*\*\*。
2. 在“选项”对话框中， 在 **GitHub** 下，单击 **Copilot**，然后单击 **Copilot Completions**。
3. 勾选“启用 接下来的编辑建议”\*\*\*\*。

## 其他阅读材料

* [GitHub Copilot 常见问题解答](https://github.com/features/copilot/#faq)

</div>

<div class="ghd-tool vscode">

## 关于 Visual Studio Code 中的 GitHub Copilot

如果使用 Visual Studio Code，GitHub Copilot 可帮助你完成各种任务，包括生成代码建议、解释编辑器中的代码工作原理以及根据你的指令提供修改建议。 您可以在 Visual Studio Code 或 GitHub 中启用或禁用 GitHub Copilot，并配置高级设置。

可以在 [VS Code 文档中了解有关场景和设置的详细信息](https://code.visualstudio.com/docs/copilot/overview#_use-cases-for-github-copilot-in-vs-code)。

## 重新绑定键盘快捷方式

使用 GitHub Copilot 时，可使用 VS Code 中的内联建议的默认键盘快捷方式。 在键盘快捷方式编辑器中，按命令名称搜索键盘快捷方式。 有关默认键盘快捷方式的列表，请参阅 [IDE 中GitHub Copilot 的键盘快捷方式](/zh/copilot/reference/keyboard-shortcuts-for-github-copilot-in-the-ide)。

或者，也可以在键盘快捷方式编辑器中将快捷方式重新绑定到每个命令。 有关详细信息，请参阅[介绍编辑快捷方式的 Visual Studio Code 文档](https://code.visualstudio.com/Docs/editor/keybindings)。

## 启用或禁用 GitHub Copilot 内联建议

可以在 GitHub Copilot 中启用或禁用 Visual Studio Code。

1. 若要配置内联建议，请在 Visual Studio Code 的标题栏中单击 **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-copilot" aria-label="copilot" role="img"><path d="M7.998 15.035c-4.562 0-7.873-2.914-7.998-3.749V9.338c.085-.628.677-1.686 1.588-2.065.013-.07.024-.143.036-.218.029-.183.06-.384.126-.612-.201-.508-.254-1.084-.254-1.656 0-.87.128-1.769.693-2.484.579-.733 1.494-1.124 2.724-1.261 1.206-.134 2.262.034 2.944.765.05.053.096.108.139.165.044-.057.094-.112.143-.165.682-.731 1.738-.899 2.944-.765 1.23.137 2.145.528 2.724 1.261.566.715.693 1.614.693 2.484 0 .572-.053 1.148-.254 1.656.066.228.098.429.126.612.012.076.024.148.037.218.924.385 1.522 1.471 1.591 2.095v1.872c0 .766-3.351 3.795-8.002 3.795Zm0-1.485c2.28 0 4.584-1.11 5.002-1.433V7.862l-.023-.116c-.49.21-1.075.291-1.727.291-1.146 0-2.059-.327-2.71-.991A3.222 3.222 0 0 1 8 6.303a3.24 3.24 0 0 1-.544.743c-.65.664-1.563.991-2.71.991-.652 0-1.236-.081-1.727-.291l-.023.116v4.255c.419.323 2.722 1.433 5.002 1.433ZM6.762 2.83c-.193-.206-.637-.413-1.682-.297-1.019.113-1.479.404-1.713.7-.247.312-.369.789-.369 1.554 0 .793.129 1.171.308 1.371.162.181.519.379 1.442.379.853 0 1.339-.235 1.638-.54.315-.322.527-.827.617-1.553.117-.935-.037-1.395-.241-1.614Zm4.155-.297c-1.044-.116-1.488.091-1.681.297-.204.219-.359.679-.242 1.614.091.726.303 1.231.618 1.553.299.305.784.54 1.638.54.922 0 1.28-.198 1.442-.379.179-.2.308-.578.308-1.371 0-.765-.123-1.242-.37-1.554-.233-.296-.693-.587-1.713-.7Z"></path><path d="M6.25 9.037a.75.75 0 0 1 .75.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 .75-.75Zm4.25.75v1.501a.75.75 0 0 1-1.5 0V9.787a.75.75 0 0 1 1.5 0Z"></path></svg>** 图标旁边的箭头，然后选择 “**配置内联建议**”。

   ![GitHub Copilot 下拉菜单中该选项的屏幕截图。 “配置内联建议”以橙色突出显示。](/assets/images/help/copilot/configure-code-completions-option-vscode.png)

2. 在“Configure Copilot Completions”对话框中，选择“Enable Completions”或“Disable Completions”\*\*\*\*\*\*\*\*。

   ![“Configure Copilot Completions”对话框的屏幕截图。 “Enable Completions”和“Disable Completions”选项以橙色突出显示。](/assets/images/help/copilot/disable-completions-dialog.png)

## 启用或禁用内联建议

可以选择在 Visual Studio Code 中启用或禁用 GitHub Copilot 的内联建议。

1. 在“文件”菜单中，导航到“首选项”，然后单击“设置”  。

   ![Visual Studio Code 设置的屏幕截图。](/assets/images/help/copilot/vsc-settings.png)
2. 在设置选项卡的左侧面板中，单击“扩展”****，然后选择“Copilot”****。
3. 在“内联建议: 启用”下，选中或取消选中该复选框以启用或禁用内联建议。

## 启用 接下来的编辑建议

可以启用 接下来的编辑建议，方法是通过 VS Code 设置 `github.copilot.nextEditSuggestions.enabled`。 有关更详细的说明，请参阅 VS Code 文档中的“[启用编辑建议](https://code.visualstudio.com/docs/copilot/ai-powered-suggestions#_enabling-edit-suggestions)”。

如果你使用 Copilot业务 计划，则为你提供计划的组织必须启用“Editor preview features”设置\*\*\*\*。 请参阅“[管理组织中GitHub Copilot的策略和功能](/zh/enterprise-cloud@latest/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-policies-for-copilot-in-your-organization#enabling-copilot-features-in-your-organization)””。

## 启用或禁用特定语言的 GitHub Copilot

可以指定要为其启用或禁用 GitHub Copilot 的语言。

1. 在 Visual Studio Code 中，单击“扩展”\*\*\*\* 选项卡，然后导航到“Copilot”\*\*\*\* 部分。 有关更多信息，请参阅[启用或禁用内联建议](#enabling-or-disabling-inline-suggestions)。
2. 在“为指定语言启用或禁用 Copilot”下，单击“在 settings.json 中编辑”\*\*\*\*。
3. 在 *settings.json* 文件中，添加或删除要启用或禁用 GitHub Copilot 的语言。 例如，要在 GitHub Copilot 中启用 Python，请将 `"python": true` 添加到列表中，确保除了最后一个列表项之外还有一个尾随逗号。

   ```json
   {
       "editor.inlineSuggest.enabled": true,
       "github.copilot.enable": {
           "*": true,
           "yaml": false,
           "plaintext": false,
           "markdown": true,
           "javascript": true,
           "python": true
       }
   }
   ```

## 撤销 GitHub Copilot 授权

Visual Studio Code 保留授权，以通过特定的 GitHub 帐户使用 GitHub Copilot。 如果您想阻止您不再可以访问的设备上的 GitHub 帐户用于 GitHub Copilot，可以撤销授权，然后再次完成授权过程。 以前使用的设备将不具有新授权。

1. 在 GitHub 任意页面的右上角，单击你的个人资料照片，然后单击“<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-gear" aria-label="gear" role="img"><path d="M8 0a8.2 8.2 0 0 1 .701.031C9.444.095 9.99.645 10.16 1.29l.288 1.107c.018.066.079.158.212.224.231.114.454.243.668.386.123.082.233.09.299.071l1.103-.303c.644-.176 1.392.021 1.82.63.27.385.506.792.704 1.218.315.675.111 1.422-.364 1.891l-.814.806c-.049.048-.098.147-.088.294.016.257.016.515 0 .772-.01.147.038.246.088.294l.814.806c.475.469.679 1.216.364 1.891a7.977 7.977 0 0 1-.704 1.217c-.428.61-1.176.807-1.82.63l-1.102-.302c-.067-.019-.177-.011-.3.071a5.909 5.909 0 0 1-.668.386c-.133.066-.194.158-.211.224l-.29 1.106c-.168.646-.715 1.196-1.458 1.26a8.006 8.006 0 0 1-1.402 0c-.743-.064-1.289-.614-1.458-1.26l-.289-1.106c-.018-.066-.079-.158-.212-.224a5.738 5.738 0 0 1-.668-.386c-.123-.082-.233-.09-.299-.071l-1.103.303c-.644.176-1.392-.021-1.82-.63a8.12 8.12 0 0 1-.704-1.218c-.315-.675-.111-1.422.363-1.891l.815-.806c.05-.048.098-.147.088-.294a6.214 6.214 0 0 1 0-.772c.01-.147-.038-.246-.088-.294l-.815-.806C.635 6.045.431 5.298.746 4.623a7.92 7.92 0 0 1 .704-1.217c.428-.61 1.176-.807 1.82-.63l1.102.302c.067.019.177.011.3-.071.214-.143.437-.272.668-.386.133-.066.194-.158.211-.224l.29-1.106C6.009.645 6.556.095 7.299.03 7.53.01 7.764 0 8 0Zm-.571 1.525c-.036.003-.108.036-.137.146l-.289 1.105c-.147.561-.549.967-.998 1.189-.173.086-.34.183-.5.29-.417.278-.97.423-1.529.27l-1.103-.303c-.109-.03-.175.016-.195.045-.22.312-.412.644-.573.99-.014.031-.021.11.059.19l.815.806c.411.406.562.957.53 1.456a4.709 4.709 0 0 0 0 .582c.032.499-.119 1.05-.53 1.456l-.815.806c-.081.08-.073.159-.059.19.162.346.353.677.573.989.02.03.085.076.195.046l1.102-.303c.56-.153 1.113-.008 1.53.27.161.107.328.204.501.29.447.222.85.629.997 1.189l.289 1.105c.029.109.101.143.137.146a6.6 6.6 0 0 0 1.142 0c.036-.003.108-.036.137-.146l.289-1.105c.147-.561.549-.967.998-1.189.173-.086.34-.183.5-.29.417-.278.97-.423 1.529-.27l1.103.303c.109.029.175-.016.195-.045.22-.313.411-.644.573-.99.014-.031.021-.11-.059-.19l-.815-.806c-.411-.406-.562-.957-.53-1.456a4.709 4.709 0 0 0 0-.582c-.032-.499.119-1.05.53-1.456l.815-.806c.081-.08.073-.159.059-.19a6.464 6.464 0 0 0-.573-.989c-.02-.03-.085-.076-.195-.046l-1.102.303c-.56.153-1.113.008-1.53-.27a4.44 4.44 0 0 0-.501-.29c-.447-.222-.85-.629-.997-1.189l-.289-1.105c-.029-.11-.101-.143-.137-.146a6.6 6.6 0 0 0-1.142 0ZM11 8a3 3 0 1 1-6 0 3 3 0 0 1 6 0ZM9.5 8a1.5 1.5 0 1 0-3.001.001A1.5 1.5 0 0 0 9.5 8Z"></path></svg> Settings”****。1. 在边栏的“Integrations”部分中，单击 <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-apps" aria-label="apps icon" role="img"><path d="M1.5 3.25c0-.966.784-1.75 1.75-1.75h2.5c.966 0 1.75.784 1.75 1.75v2.5A1.75 1.75 0 0 1 5.75 7.5h-2.5A1.75 1.75 0 0 1 1.5 5.75Zm7 0c0-.966.784-1.75 1.75-1.75h2.5c.966 0 1.75.784 1.75 1.75v2.5a1.75 1.75 0 0 1-1.75 1.75h-2.5A1.75 1.75 0 0 1 8.5 5.75Zm-7 7c0-.966.784-1.75 1.75-1.75h2.5c.966 0 1.75.784 1.75 1.75v2.5a1.75 1.75 0 0 1-1.75 1.75h-2.5a1.75 1.75 0 0 1-1.75-1.75Zm7 0c0-.966.784-1.75 1.75-1.75h2.5c.966 0 1.75.784 1.75 1.75v2.5a1.75 1.75 0 0 1-1.75 1.75h-2.5a1.75 1.75 0 0 1-1.75-1.75ZM3.25 3a.25.25 0 0 0-.25.25v2.5c0 .138.112.25.25.25h2.5A.25.25 0 0 0 6 5.75v-2.5A.25.25 0 0 0 5.75 3Zm7 0a.25.25 0 0 0-.25.25v2.5c0 .138.112.25.25.25h2.5a.25.25 0 0 0 .25-.25v-2.5a.25.25 0 0 0-.25-.25Zm-7 7a.25.25 0 0 0-.25.25v2.5c0 .138.112.25.25.25h2.5a.25.25 0 0 0 .25-.25v-2.5a.25.25 0 0 0-.25-.25Zm7 0a.25.25 0 0 0-.25.25v2.5c0 .138.112.25.25.25h2.5a.25.25 0 0 0 .25-.25v-2.5a.25.25 0 0 0-.25-.25Z"></path></svg>“Applications”****。1. 单击“授权的 OAuth 应用”选项卡。

   ![“应用程序”页的屏幕截图。 标有“授权的 OAuth 应用”的选项卡以橙色边框突出显示。](/assets/images/help/settings/settings-authorized-oauth-apps-tab.png)
2. 单击“VS Code 的 GitHub”\*\*\*\* 右侧的“...”****，然后单击“撤销”****。
   授权访问 GitHub 应用程序
3. 如果列出了 **GitHub Copilot 扩展**，请单击“撤销”。\*\*\*\*

撤销授权后，Visual Studio Code 将能够在当前会话中继续使用 GitHub Copilot 最多 30 分钟。 之后，你将需要重新授权 GitHub Copilot 以再次在 Visual Studio Code 中使用。

## 重新授权 GitHub Copilot

撤销授权后，如果要继续使用 GitHub Copilot，则需要完成重新授权过程。

1. 在 Visual Studio Code 左下角，单击**帐户**图标，将鼠标悬停在用户名上，然后单击“退出登录”\*\*\*\*。

   ![Visual Studio Code 中的菜单的屏幕截图。 “退出登录”选项以深橙色框出。](/assets/images/help/copilot/vsc-sign-out.png)

2. 在“Visual Studio Code”弹出窗口中，单击“退出登录”\*\*\*\*。

3. 在 Visual Studio Code 左下角，单击**帐户**图标，将鼠标悬停在用户名上，然后单击“使用 GitHub 登录以使用 GitHub Copilot”\*\*\*\*。

   ![Visual Studio Code 中的帐户菜单的屏幕截图。 “使用 GitHub 登录以使用 GitHub Copilot (1)”选项以深橙色框出。](/assets/images/help/copilot/vsc-sign-in.png)

4. 在浏览器中，GitHub 将请求 GitHub Copilot 所需的权限。 要批准这些权限，请单击“继续”\*\*\*\*。

5. 在“打开 Visual Studio Code?” 弹出窗口中，单击“打开 Visual Studio Code”\*\*\*\*。

## 在 Copilot 上配置 GitHub.com 设置

如果您使用的是 Copilot Pro、Copilot Pro+ 或 Copilot Max 计划，则可以选择允许或禁止与公开可用代码匹配的内联建议。
你还可以允许或阻止收集和保留你输入的提示以及 Copilot 提供的建议。 可在个人设置 GitHub.com中配置此设置。 请参阅“[以个人订阅者身份管理 GitHub Copilot 策略](/zh/copilot/configuring-github-copilot/configuring-your-personal-github-copilot-settings-on-githubcom)”。

## 在 GHE.com 上对账户进行身份验证

如果在 Copilot 上使用 托管用户帐户 的 GHE.com 计划，则需要在登录之前更新一些设置。 请参阅 [在 GHE.com 上将 GitHub Copilot 与帐户配合使用](/zh/copilot/managing-copilot/configure-personal-settings/using-github-copilot-with-an-account-on-ghecom)。

## 其他阅读材料

* [VS Code 中的 GitHub Copilot](https://code.visualstudio.com/docs/copilot/overview)
* [GitHub Copilot 常见问题解答](https://github.com/features/copilot/#faq)

</div>

<div class="ghd-tool vimneovim">

## 在 Vim/Neovim 中配置 GitHub Copilot

有关在 Vim/Neovim 中配置 GitHub Copilot 的指导，请运行以下命令，在 Vim/Neovim 中调用 GitHub Copilot 文档：

```
:help copilot
```

## 重新绑定键盘快捷方式

使用 GitHub Copilot 为每个特定命令使用首选键盘快捷方式时，可以在 Vim/Neovim 中重新绑定键盘快捷方式。 有关详细信息，请参阅 Neovim 文档中的[映射](https://neovim.io/doc/user/map.html)一文。

## 在 Copilot 上配置 GitHub.com 设置

如果您使用的是 Copilot Pro、Copilot Pro+ 或 Copilot Max 计划，则可以选择允许或禁止与公开可用代码匹配的内联建议。
你还可以允许或阻止收集和保留你输入的提示以及 Copilot 提供的建议。 可在个人设置 GitHub.com中配置此设置。 请参阅“[以个人订阅者身份管理 GitHub Copilot 策略](/zh/copilot/configuring-github-copilot/configuring-your-personal-github-copilot-settings-on-githubcom)”。

## 在 GHE.com 上对账户进行身份验证

如果在 Copilot 上使用 托管用户帐户 的 GHE.com 计划，则需要在登录之前更新一些设置。 请参阅 [在 GHE.com 上将 GitHub Copilot 与帐户配合使用](/zh/copilot/managing-copilot/configure-personal-settings/using-github-copilot-with-an-account-on-ghecom)。

## 其他阅读材料

* [GitHub Copilot 常见问题解答](https://github.com/features/copilot/#faq)

</div>

<div class="ghd-tool xcode">

## 关于 Xcode 中的 GitHub Copilot

如果使用 Xcode，GitHub Copilot 可帮助你完成各种任务，包括生成代码建议、解释编辑器中的代码工作原理以及提供代码修复建议。 安装后，您可以开启或关闭 GitHub Copilot，并可以在 Xcode 或 GitHub 中配置高级设置。

## Prerequisites

要为 Xcode 配置 GitHub Copilot，必须安装 GitHub Copilot 扩展。 请参阅 [在环境中安装 GitHub Copilot 扩展](/zh/copilot/managing-copilot/configure-personal-settings/installing-the-github-copilot-extension-in-your-environment?tool=xcode)。

## 重新绑定键盘快捷方式

使用 GitHub Copilot 时，可以在 Xcode 中使用默认键盘快捷方式获取内联建议。 有关默认键盘快捷方式的列表，请参阅 [IDE 中GitHub Copilot 的键盘快"files.associations": {
    "**/somefolder/*.*": "php"
}
  // The default language mode that is assigned to new files.
  "files.defaultLanguage": "html"

在编辑器中使用 GitHub Copilot 获取代码建议。

<style> .button-container { display： flex; gap： 10px; } </style><div class="button-container">                  <a href="https://github.com/copilot?ref_product=copilot&ref_type=trial&ref_style=button&ref_plan=free" target="_blank" class="btn btn-primary mt-3 mr-3 no-underline">                      <span>免费开始使用</span> <svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-link-external" aria-label="link external icon" role="img"><path d="M3.75 2h3.5a.75.75 0 0 1 0 1.5h-3.5a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-3.5a.75.75 0 0 1 1.5 0v3.5A1.75 1.75 0 0 1 12.25 14h-8.5A1.75 1.75 0 0 1 2 12.25v-8.5C2 2.784 2.784 2 3.75 2Zm6.854-1h4.146a.25.25 0 0 1 .25.25v4.146a.25.25 0 0 1-.427.177L13.03 4.03 9.28 7.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.75-3.75-1.543-1.543A.25.25 0 0 1 10.604 1Z"></path></svg></a>

<div class="ghd-tool vscode">
<a href="vscode://GitHub.Copilot-Chat?ref_product=copilot&ref_type=engagement&ref_style=button" target="_blank" class="btn btn-primary mt-3 mr-3 no-underline">        <span>在 Visual Studio Code 中打开</span><svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-link-external" aria-label="link external icon" role="img"><path d="M3.75 2h3.5a.75.75 0 0 1 0 1.5h-3.5a.25.25 0 0 0-.25.25v8.5c0 .138.112.25.25.25h8.5a.25.25 0 0 0 .25-.25v-3.5a.75.75 0 0 1 1.5 0v3.5A1.75 1.75 0 0 1 12.25 14h-8.5A1.75 1.75 0 0 1 2 12.25v-8.5C2 2.784 2.784 2 3.75 2Zm6.854-1h4.146a.25.25 0 0 1 .25.25v4.146a.25.25 0 0 1-.427.177L13.03 4.03 9.28 7.78a.751.751 0 0 1-1.042-.018.751.751 0 0 1-.018-1.042l3.75-3.75-1.543-1.543A.25.25 0 0 1 10.604 1Z"></path></svg></a>
</div>

</div>

<div class="ghd-tool jetbrains">

## 简介

本指南将演示如何从 JetBrains IDE 中的 GitHub Copilot 获取编码建议。 要查看其他常用编码环境的说明，请使用页面顶部的工具切换器。

本指南中的示例使用 Java，但其他语言的工作方式类似。

有关详细信息，请参阅“[IDE 中的 GitHub Copilot 代码建议](/zh/copilot/concepts/completions/code-suggestions?tool=jetbrains)”。

## Prerequisites

* ```
            **对 Copilot 的访问权限**。 要在 JetBrains 中使用 GitHub Copilot，你需要通过 免费Copilot 获得有限访问权限，或者通过付费的 Copilot 计划获得完全访问权限。 请参阅“[AUTOTITLE](/copilot/about-github-copilot/what-is-github-copilot#getting-access-to-copilot)”。
  ```

* **兼容的 JetBrains IDE**。 若要在 JetBrains 中使用 GitHub Copilot，必须安装兼容的 JetBrains IDE。 GitHub Copilot 与以下 IDE 兼容：

  * IntelliJ IDEA（旗舰版、社区版、教育版）
  * Android Studio
  * AppCode
  * CLion
  * Code With Me 来宾
  * DataGrip
  * DataSpell
  * GoLand
  * JetBrains 客户端
  * MPS
  * PhpStorm
  * PyCharm（专业版、社区版、教育版）
  * Rider
  * RubyMine
  * RustRover
  * WebStorm
  * Writerside

  请参阅 [JetBrains IDE](https://www.jetbrains.com/products/?ref_product=copilot\&ref_type=engagement\&ref_style=button) 工具查找器进行下载。

* 最新版本的 GitHub Copilot 扩展\*\*\*\*。 请参阅 JetBrains Marketplace 中的 [GitHub Copilot 插件](https://plugins.jetbrains.com/plugin/17718-github-copilot?ref_product=copilot\&ref_type=engagement\&ref_style=text)。 有关安装说明，请参阅“[在环境中安装 GitHub Copilot 扩展](/zh/copilot/configuring-github-copilot/installing-the-github-copilot-extension-in-your-environment)”。

* 在 JetBrains IDE 中登录到 GitHub\*\*\*\*。 有关身份验证说明，请参阅“[在环境中安装 GitHub Copilot 扩展](/zh/copilot/configuring-github-copilot/installing-the-github-copilot-extension-in-your-environment?tool=jetbrains#installing-the-github-copilot-plugin-in-your-jetbrains-ide)”。

## 获取代码建议

GitHub Copilot 会在你键入时提供编码建议。 例如，在一个 Java 文件中，键入 `class Test` 以创建一个类。

GitHub Copilot 将自动以灰色文本建议类正文。 要接受建议，请按 <kbd>Tab</kbd>。

也可以在注释内使用自然语言描述要执行的操作，Copilot 会提供代码建议以实现你的目标。 例如，在一个 Java 文件中键入此注释：

```java copy
// find all images without alternate text
// and give them a red border
void process () {
```

GitHub Copilot 会自动提供代码建议。 要接受建议，请按 <kbd>Tab</kbd>。

GitHub Copilot 将尝试与代码的上下文和样式匹配。 始终可以编辑建议的代码。

> \[!TIP]
> 如果从 Copilot 收到有限的建议或未收到任何建议，则表明你可能启用了重复检测。 有关重复检测的详细信息，请参阅 [以个人订阅者身份管理 GitHub Copilot 策略](/zh/copilot/configuring-github-copilot/configuring-your-personal-github-copilot-settings-on-githubcom#enabling-or-disabling-suggestions-matching-public-code)。

## 显示替代建议

对于任何给定的输入，GitHub Copilot 可以提供多个建议。 可以选择要使用的建议，或拒绝所有建议。

例如，在一个 Java 文件中键入下面这一行内容，然后按 <kbd>Enter</kbd>：

```java copy
private int calculateDaysBetweenDates(Date date1,
```

GitHub Copilot 将向你显示建议。

现在，将鼠标悬停在建议上方，以显示用来选择建议的 GitHub Copilot 控件。 要显示下一批或上一批建议，请单击控件中的向前或向后箭头按钮。

也可以使用键盘快捷方式显示替代建议：

| OS                           | 查看下一个建议 | 查看上一个建议 |
| :--------------------------- | :------ | :------ |
| macOS                        |         |         |
| <kbd>选择</kbd>+<kbd>]</kbd>   |         |         |
| <kbd>选择</kbd>+<kbd>\[</kbd>  |         |         |
| Windows 或 Linux              |         |         |
| <kbd>Alt</kbd>+<kbd>]</kbd>  |         |         |
| <kbd>Alt</kbd>+<kbd>\[</kbd> |         |         |

要接受建议，请单击 Copilot 命令面板中的“接受”，或按 <kbd>Tab</kbd>。要拒绝所有建议，请按 <kbd>Esc</kbd>。

## 在新选项卡中显示多个建议

如果不想使用 GitHub Copilot 提供的任何初始建议，可以在新选项卡中显示多个建议。

例如，在一个 Java 文件中键入下面这一行内容：

```java copy
private int calculateDaysBetweenDates(Date date1,
```

GitHub Copilot 将向你显示建议。

要打开一个具有多个其他建议的新选项卡，请使用如下键盘快捷方式，然后单击**打开 GitHub Copilot**：

| OS                                            | 打开多个建议 |
| :-------------------------------------------- | :----- |
| macOS                                         |        |
| <kbd>命令键</kbd>+<kbd>Shift键</kbd>+<kbd>A</kbd> |        |
| Windows 或 Linux                               |        |
| <kbd>Ctrl</kbd>+<kbd>进入</kbd>                 |        |

要接受建议，请单击建议下方的“**接受建议编号**”。 若要拒绝所有建议，请关闭选项卡。

## 接受部分建议

如果不想接受 GitHub Copilot 的完整建议，可以接受下一个单词或下一行建议。

例如，在一个 Java 文件中键入下面这一行内容：

```java copy
private int calculateDaysBetweenDates(Date date1,
```

GitHub Copilot 将以灰色文本显示建议。 具体的建议可能会有所不同。

现在，将鼠标悬停在建议上方，以显示用来选择建议的 GitHub Copilot 控件。 要只接受建议的下一个单词，请单击控件中的“接受单词”。\*\*\*\*

或者，也可以使用键盘快捷方式接受建议的下一个单词：

| OS                                        | 接受下一个字词 | 接受下一行 |
| :---------------------------------------- | :------ | :---- |
| macOS                                     |         |       |
| <kbd>命令</kbd>+<kbd>→</kbd>                |         |       |
| <kbd>命令</kbd>+<kbd>控制</kbd>+<kbd>→</kbd>  |         |       |
| Windows 或 Linux                           |         |       |
| <kbd>控制</kbd>+<kbd>→</kbd>                |         |       |
| <kbd>控制</kbd>+<kbd>Alt</kbd>+<kbd>→</kbd> |         |       |

如果希望接受下一行建议，则需要为命令 `editor.action.inlineSuggest.acceptNextLine` 设置自定义键盘快捷方式。 有关设置自定义键盘快捷方式的详细信息，请参阅 [在环境中配置 GitHub Copilot](/zh/copilot/configuring-github-copilot/configuring-github-copilot-in-your-environment)。

</div>

<div class="ghd-tool visualstudio">

## 简介

本指南将演示如何从 GitHub Copilot for Windows 中的 Visual Studio 获取编码建议。 要查看其他常用编码环境的说明，请使用页面顶部的工具切换器。

本指南中的示例使用 C#，但其他语言的工作方式类似。

有关详细信息，请参阅“[IDE 中的 GitHub Copilot 代码建议](/zh/copilot/concepts/completions/code-suggestions?tool=visualstudio)”。

## Prerequisites

* ```
            **对 Copilot 的访问权限**。 要在 GitHub Copilot 内的 GitHub Copilot 中使用 Visual Studio，你需要通过 免费Copilot 获得有限访问权限，或者通过付费的 Copilot 计划获得完全访问权限。 请参阅“[AUTOTITLE](/copilot/about-github-copilot/what-is-github-copilot#getting-access-to-copilot)”。
  ```

* ```
            **Visual Studio 的兼容版本**。 要在 GitHub Copilot 中使用 Visual Studio，必须安装 Visual Studio for Windows 版本 2022 17.8 或更高版本。 有关更多信息，请参阅 Microsoft 文档中的“[安装 Visual Studio](https://learn.microsoft.com/en-us/visualstudio/install/install-visual-studio?ref_product=copilot&ref_type=engagement&ref_style=text)”。
  ```

* ```
            **适用于 GitHub Copilot 的 Visual Studio 扩展**。 有关如何安装 Copilot 扩展的说明，请参阅 Microsoft 文档中的“[在 Visual Studio 中安装 GitHub Copilot](https://learn.microsoft.com/visualstudio/ide/visual-studio-github-copilot-install-and-states?ref_product=copilot&ref_type=engagement&ref_style=text)”。
  ```

* ```
            **将 GitHub 帐户添加到 Visual Studio**。 请参阅 Microsoft 文档中的[将 GitHub 帐户添加到 Visual Studio 密钥链](https://learn.microsoft.com/en-us/visualstudio/ide/work-with-github-accounts?ref_product=copilot&ref_type=engagement&ref_style=text)。
  ```

## 获取代码建议

GitHub Copilot 会在你键入时提供编码建议。 例如，在一个 C# 文件中键入此函数签名：

```csharp copy
int CalculateDaysBetweenDates(
```

GitHub Copilot 会自动以灰色文本建议整个函数正文。 要接受建议，请按 <kbd>Tab</kbd>。

也可以在注释内使用自然语言描述要执行的操作，Copilot 会提供代码建议以实现你的目标。 例如，在一个 C# 文件中键入此注释：

```csharp copy
using System.Xml.Linq;

var doc = XDocument.Load("index.xhml");

// find all images
```

GitHub Copilot 将建议函数的实现。 要接受建议，请按 <kbd>Tab</kbd>。

> \[!TIP]
> 如果从 Copilot 收到有限的建议或未收到任何建议，则表明你可能启用了重复检测。 有关重复检测的详细信息，请参阅 [以个人订阅者身份管理 GitHub Copilot 策略](/zh/copilot/configuring-github-copilot/configuring-your-personal-github-copilot-settings-on-githubcom#enabling-or-disabling-suggestions-matching-public-code)。

## 显示替代建议

对于任何给定的输入，GitHub Copilot 可以提供多个建议。 可以选择要使用的建议，或拒绝所有建议。

例如，在一个 C# 文件中键入此函数签名：

```csharp copy
int CalculateDaysBetweenDates(
```

GitHub Copilot 将向你显示建议。

现在，将鼠标悬停在建议上方，以显示用来选择建议的 GitHub Copilot 控件。 要显示下一批或上一批建议，请单击控件中的向前或向后箭头按钮。

或者，也可以按键盘上的 <kbd>Alt</kbd>+<kbd>.</kbd> （或 <kbd>Alt</kbd>+<kbd>,</kbd>），以显示替代建议。

要接受建议，请单击 Copilot 命令面板中的“接受”，或按 <kbd>Tab</kbd>。要拒绝所有建议，请按 <kbd>Esc</kbd>。

## 获取注释建议

> \[!NOTE] Visual Studio 17.14 预览版 2 及更高版本中提供了注释建议。

GitHub Copilot 可以通过分析你编写的代码并生成描述代码用途的注释来提供代码注释建议。 对于 免费Copilot 用户，注释建议会计入每月 副驾驶聊天 使用量，而不是代码建议使用量。

注释建议支持以下语言：

* C#
* C++

### 启用注释建议

若要启用注释建议，需要在 Visual Studio 中配置注释样式。

#### 对于 C++

1. 在 Visual Studio 的“工具”菜单中，单击“选项”\*\*\*\*\*\*\*\*。
2. 在左侧面板中，单击“文本编辑器”\*\*\*\*。
3. 单击 **C++**，然后单击 **“代码样式**”。
4. 在 **“代码样式”** 标题下，单击“ **常规**”。
5. 在“Comments”下，从下拉列表中选择“Xml Doc Comments”\*\*\*\*。
6. 选择“编写注释时在新行的开头插入现有注释风格”和“继续进行单行注释”\*\*\*\*****。 然后点击**OK**。
7. 在**Options**选项卡中的左侧面板中，单击**GitHub**。
8. 单击 **“Copilot**”，然后单击 **“编辑器**”。
9. 选择**启用 AI 生成的描述，以在支持的语言中自动插入文档注释**。

#### 对于 C\#

1. 在 Visual Studio 的“工具”菜单中，单击“选项”\*\*\*\*\*\*\*\*。
2. 在左侧面板中，单击“ **语言**”。
3. 单击 **C#**，然后单击 **“更多设置”**，然后单击 **“高级**”。
4. 在“注释”下，选择**为 /// 生成 XML 文档注释**、**编写 // 注释时，请在新行的开头插入 //** 和 **编写 /\*\*/ 注释时在新行开头插入 \***。 然后点击**OK**。
5. 在**Options**选项卡中的左侧面板中，单击**GitHub**。
6. 单击 **“Copilot**”，然后单击 **“编辑器**”。
7. 选择**启用 AI 生成的描述，以在支持的语言中自动插入文档注释**。

### 使用注释建议

若要启动注释建议，请在要注释的代码之前键入编写代码所用的语言对应的标准注释起始符（例如 `///`），然后等待建议显示。

要接受建议，请按 <kbd>Tab</kbd>。若要修改建议，请按 <kbd>Alt</kbd>+<kbd>/</kbd>。 若要拒绝建议，请按 <kbd>Esc</kbd>。

## 导航和接受 接下来的编辑建议

基于你正在进行的编辑，Copilot 将预测你接下来可能进行编辑的位置，并给出相应的补全建议。

可以使用 <kbd>Tab</kbd> 浏览建议的代码更改，从而更轻松地找到下一个相关编辑，而无需手动搜索文件或引用。 再次按 <kbd>Tab</kbd> 可接受建议。

装订线中的箭头表示有可用的编辑建议。 单击箭头以访问提供键盘快捷方式的编辑建议菜单。 如果编辑建议在当前编辑器视图之外，则箭头将向上或向下指，以指示下一条建议的位置。

</div>

<div class="ghd-tool vscode">

## 简介

本指南将演示如何从 GitHub Copilot 中的 Visual Studio Code 获取编码建议。 要查看其他常用编码环境的说明，请使用页面顶部的工具切换器。

本指南中的示例使用 JavaScript，但其他语言的工作方式类似。

有关详细信息，请参阅“[IDE 中的 GitHub Copilot 代码建议](/zh/copilot/concepts/completions/code-suggestions?tool=vscode)”。

## Prerequisites

* ```
            **对 Copilot 的访问权限**。 要在 GitHub Copilot 中使用 Visual Studio Code，你需要通过 免费Copilot 获得有限访问权限，或者通过付费的 Copilot 计划获得完全访问权限。 请参阅“[AUTOTITLE](/copilot/about-github-copilot/what-is-github-copilot#getting-access-to-copilot)”。
  ```

* ```
            **在 GitHub 中登录 Visual Studio Code**。 请参阅 GitHub Copilot 文档中的[在 Visual Studio Code 中设置 VS Code](https://code.visualstudio.com/docs/copilot/setup?ref_product=copilot&ref_type=engagement&ref_style=text)。
  ```

* **Visual Studio Code**。 若要在 GitHub Copilot 中使用 Visual Studio Code，必须安装 Visual Studio Code。 有关详细信息，请参阅 [Visual Studio Code 下载页面](https://code.visualstudio.com/Download?ref_product=copilot\&ref_type=engagement\&ref_style=text)。

* **Copilot 中的 Visual Studio Code**。 当你首次在 GitHub Copilot 中设置 Visual Studio Code 时，系统会自动安装所需的扩展。 你无需手动下载或安装它们。 有关详细说明，请参阅 GitHub Copilot 文档中的[在 Visual Studio Code 中设置 Visual Studio Code](https://code.visualstudio.com/docs/copilot/setup?ref_product=copilot\&ref_type=engagement\&ref_style=text)。

## 获取代码建议

GitHub Copilot 会在你键入时提供编码建议。 例如，在一个 JavaScript 文件中键入此函数标头：

```javascript copy
function calculateDaysBetweenDates(begin, end) {
```

GitHub Copilot 会自动建议函数的剩余部分。 要接受建议，请按 <kbd>Tab</kbd>。

也可以在注释内使用自然语言描述要执行的操作，Copilot 会提供代码建议以实现你的目标。 例如，在一个 JavaScript 文件中键入此注释：

```javascript copy
// write a function to
// find all images without alternate text
// and give them a red border
```

GitHub Copilot 会自动提供代码建议。 要接受建议，请按 <kbd>Tab</kbd>。

> \[!TIP]
> 如果从 Copilot 收到有限的建议或未收到任何建议，则表明你可能启用了重复检测。 有关重复检测的详细信息，请参阅 [以个人订阅者身份管理 GitHub Copilot 策略](/zh/copilot/configuring-github-copilot/configuring-your-personal-github-copilot-settings-on-githubcom#enabling-or-disabling-suggestions-matching-public-code)。

## 显示替代建议

对于任何给定的输入，GitHub Copilot 可以提供多个建议。 可以选择要使用的建议，或拒绝所有建议。

例如，在一个 JavaScript 文件中键入此函数标头，然后按 <kbd>Enter</kbd>：

```javascript copy
function calculateDaysBetweenDates(begin, end) {
```

GitHub Copilot 将向你显示建议。

现在，将鼠标悬停在建议上方，以显示用来选择建议的 GitHub Copilot 控件。 要显示下一批或上一批建议，请单击控件中的向前或向后箭头按钮。

也可以使用键盘快捷方式显示替代建议：

| OS                                        | 查看下一个建议 | 查看上一个建议 |
| :---------------------------------------- | :------ | :------ |
| macOS                                     |         |         |
| <kbd>Option (⌥) 或 Alt</kbd>+<kbd>]</kbd>  |         |         |
| <kbd>Option (⌥) 或 Alt</kbd>+<kbd>\[</kbd> |         |         |
| Windows 或 Linux                           |         |         |
| <kbd>Alt</kbd>+<kbd>]</kbd>               |         |         |
| <kbd>Alt</kbd>+<kbd>\[</kbd>              |         |         |

要接受建议，请单击 Copilot 命令面板中的“接受”，或按 <kbd>Tab</kbd>。要拒绝所有建议，请按 <kbd>Esc</kbd>。

## 在新选项卡中显示多个建议

如果不想使用 GitHub Copilot 提供的任何初始建议，可以在新选项卡中显示多个建议。

例如，在一个 JavaScript 文件中键入此函数标头，然后按 <kbd>Enter</kbd>：

```javascript copy
function calculateDaysBetweenDates(begin, end) {
```

GitHub Copilot 将向你显示建议。 现在，按 <kbd>Ctrl</kbd>+<kbd>Enter</kbd>，以打开具有多个其他选项的新选项卡。

要接受建议，请单击建议下方的“**接受建议编号**”。 若要拒绝所有建议，请关闭选项卡。

## 接受部分建议

如果不想接受 GitHub Copilot 的完整建议，可以接受下一个单词或下一行建议。

例如，在一个 JavaScript 文件中键入此函数标头，然后按 <kbd>Enter</kbd>：

```javascript copy
function calculateDaysBetweenDates(begin, end) {
```

GitHub Copilot 会自动以灰色文本建议整个函数正文。 具体的建议可能会有所不同。

现在，将鼠标悬停在建议上方，以显示用来选择建议的 GitHub Copilot 控件。 要只接受建议的下一个单词，请单击控件中的“接受单词”。\*\*\*\*

或者，也可以使用键盘快捷方式接受建议的下一个单词：

| OS                         | 接受下一个字词 |
| :------------------------- | :------ |
| macOS                      |         |
| <kbd>命令</kbd>+<kbd>→</kbd> |         |
| Windows 或 Linux            |         |
| <kbd>控制</kbd>+<kbd>→</kbd> |         |

如果希望接受下一行建议，则需要为命令 `editor.action.inlineSuggest.acceptNextLine` 设置自定义键盘快捷方式。 有关设置自定义键盘快捷方式的详细信息，请参阅 [在环境中配置 GitHub Copilot](/zh/copilot/configuring-github-copilot/configuring-github-copilot-in-your-environment)。

## 导航和接受 接下来的编辑建议

下一个编辑建议 根据正在进行的更改预测可能需要在何处进行何种编辑。

可以使用 <kbd>Tab</kbd> 浏览建议的代码更改，从而更轻松地找到下一个相关编辑，而无需手动搜索文件或引用。 再次按 <kbd>Tab</kbd> 可接受建议。

装订线中的箭头表示有可用的编辑建议。 将鼠标悬停在箭头上以access编辑建议菜单，该菜单提供键盘快捷方式和设置选项。 如果编辑建议在当前编辑器视图之外，则箭头将向上或向下指，以指示下一条建议的位置。

![Visual Studio Code 中的装订线菜单的屏幕截图。 箭头用深橙色突出显示。](/assets/images/help/copilot/vsc-advanced-code-completion-menu.png)

有关更多详细信息和示例，请参阅 GitHub Copilot 文档中的 [VS Code 中的 Visual Studio Code 内联建议](https://code.visualstudio.com/docs/copilot/ai-powered-suggestions)。

## 更改 AI 模型

可以更改用于生成内联建议的大型语言模型。 有关详细信息，请参阅“[更改适用于 GitHub Copilot 内联建议的 AI 模型](/zh/copilot/how-tos/use-ai-models/change-the-completion-model)”。

</div>

<div class="ghd-tool vimneovim">

## 简介

本指南将演示如何从 Vim/Neovim 中的 GitHub Copilot 获取编码建议。 要查看其他常用编码环境的说明，请使用页面顶部的工具切换器。

## Prerequisites

* ```
            **对 Copilot 的访问权限**。 要在 Vim/Neovim 中使用 GitHub Copilot，你需要通过 免费Copilot 获得有限访问权限，或者通过付费的 Copilot 计划获得完全访问权限。 请参阅“[AUTOTITLE](/copilot/about-github-copilot/what-is-github-copilot#getting-access-to-copilot)”。
  ```

* **Vim/Neovim 的兼容版本**。 要在 Vim/Neovim 中使用 GitHub Copilot，必须安装 Vim 版本 9.0.0185 / Neovim 版本 0.6 或更高版本以及 Node.js 版本 18 或更高版本。 有关详细信息，请参阅 [Vim](https://vimhelp.org/) / [Neovim 文档](https://neovim.io/doc/)和 [Node.js 网站](https://nodejs.org/en/)。

* **适用于 Vim/Neovim 的 GitHub Copilot 扩展**。 要在 Vim/Neovim 中使用 GitHub Copilot，必须安装 GitHub Copilot 插件。 有关详细信息，请参阅 [在环境中安装 GitHub Copilot 扩展](/zh/copilot/configuring-github-copilot/installing-the-github-copilot-extension-in-your-environment)。

## 了解如何在 Vim/Neovim 中使用 GitHub Copilot

当你在 Vim/Neovim 中键入时，GitHub Copilot 会提供建议内联。 要接受建议，请按 <kbd>Tab</kbd> 键。

有关如何在 Vim/Neovim 中使用 GitHub Copilot 的更多信息和指导，请运行如下命令，以查看插件文档：

```shell copy
:help copilot
```

</div>

<div class="ghd-tool azure_data_studio">

## 简介

本指南演示如何在 Azure Data Studio 中获取 GitHub Copilot 的编码建议。 要查看其他常用编码环境的说明，请使用页面顶部的工具切换器。

## Prerequisites

* ```
            **对 Copilot 的访问权限**。 要在 Azure Data Studio 中使用 GitHub Copilot，你需要通过 免费Copilot 获得有限访问权限，或者通过付费的 Copilot 计划获得完全访问权限。 请参阅“[AUTOTITLE](/copilot/about-github-copilot/what-is-github-copilot#getting-access-to-copilot)”。
  ```

* **兼容版本的 Azure Data Studio**。 若要在 Azure Data Studio 中使用 GitHub Copilot，您必须安装 Azure Data Studio 1.44.0 或以上版本。 有关详细信息，请参阅 Azure Data Studio 文档中的 [Azure Data Studio 下载页](https://docs.microsoft.com/sql/azure-data-studio/download-azure-data-studio)。

* **GitHub Copilot 扩展适用于 Azure Data Studio**。 若要在 Azure Data Studio 中使用 GitHub Copilot，必须安装 GitHub Copilot 扩展。 有关详细信息，请参阅 [在环境中安装 GitHub Copilot 扩展](/zh/copilot/configuring-github-copilot/installing-the-github-copilot-extension-in-your-environment)。

## 获取代码建议

在 Azure Data Studio 中创建 SQL 数据库时，GitHub Copilot 可以提供内联建议。 例如，如果要编写联接两个表的查询，Copilot 可以建议联接条件，包括打开的编辑器中的列、工作区中的其他文件和常见语法模式。

在一个 SQL 文件中，键入如下查询：

```sql copy
SELECT [UserId], [Red], [Orange], [Yellow], [Green], [Blue], [Purple], [Rainbow]
FROM [Tag].[Scoreboard]
INNER JOIN
```

GitHub Copilot 将自动以灰色文本建议联接条件。 具体的建议可能会有所不同。 要接受建议，请按 <kbd>Tab</kbd>。

也可以在注释内使用自然语言描述要执行的操作，Copilot 会提供代码建议以实现你的目标。 例如，在一个 SQL 文件中键入此注释：

```sql copy
SELECT TokenColor, COUNT(UserID) AS UserCount
FROM Tag.Users
GROUP BY TokenColor
-- pivot that query on tokencolor for Purple, Blue, Green, Yellow, Orange, Red
-- and rename the columns to match the colors
SELECT [Purple], [Blue], [Green], [Yellow], [Orange], [Red]
```

GitHub Copilot 会自动提供代码建议。 要接受建议，请按 <kbd>Tab</kbd>。

> \[!TIP]
> 如果从 Copilot 收到有限的建议或未收到任何建议，则表明你可能启用了重复检测。 有关重复检测的详细信息，请参阅 [以个人订阅者身份管理 GitHub Copilot 策略](/zh/copilot/configuring-github-copilot/configuring-your-personal-github-copilot-settings-on-githubcom#enabling-or-disabling-suggestions-matching-public-code)。

## 显示替代建议

对于某些建议，GitHub Copilot 可能会提供多个替代方法。 可以选择要采用的建议，或拒绝所有建议。

例如，在一个 SQL 文件中键入此查询：

```sql copy
SELECT [UserId], [Red], [Orange], [Yellow], [Green], [Blue], [Purple], [Rainbow]
FROM [Tag].[Scoreboard]
INNER JOIN
```

GitHub Copilot 将向你显示建议。

现在，将鼠标悬停在建议上方，以显示用来选择建议的 GitHub Copilot 控件。 要显示下一批或上一批建议，请单击控件中的向前或向后箭头按钮。

也可以使用键盘快捷方式显示替代建议：

| OS                           | 查看下一个建议 | 查看上一个建议 |
| :--------------------------- | :------ | :------ |
| macOS                        |         |         |
| <kbd>选择</kbd>+<kbd>\[</kbd>  |         |         |
| <kbd>选择</kbd>+<kbd>]</kbd>   |         |         |
| Windows 或 Linux              |         |         |
| <kbd>Alt</kbd>+<kbd>\[</kbd> |         |         |
| <kbd>Alt</kbd>+<kbd>]</kbd>  |         |         |

要接受建议，请单击 Copilot 控件中的“接受”，或者按 <kbd>Tab</kbd>。要拒绝所有建议，请按 <kbd>Esc</kbd>。

## 接受部分建议

如果不想接受 GitHub Copilot 的完整建议，可以接受下一个单词或下一行建议。

例如，在一个 SQL 文件中键入此查询：

```sql copy
SELECT [UserId], [Red], [Orange], [Yellow], [Green], [Blue], [Purple], [Rainbow]
FROM [Tag].[Scoreboard]
INNER JOIN
```

GitHub Copilot 将以灰色文本显示建议。 具体的建议可能会有所不同。

现在，将鼠标悬停在建议上方，以显示用来选择建议的 GitHub Copilot 控件。 要只接受建议的下一个单词，请单击控件中的“接受单词”。\*\*\*\*

或者，也可以使用键盘快捷方式接受建议的下一个单词：

| OS                         | 接受下一个字词 |
| :------------------------- | :------ |
| macOS                      |         |
| <kbd>命令</kbd>+<kbd>→</kbd> |         |
| Windows 或 Linux            |         |
| <kbd>控制</kbd>+<kbd>→</kbd> |         |

如果要接受下一行建议，则需要为命令 `editor.action.inlineSuggest.acceptNextLine` 设置自定义键盘快捷键。 有关设置自定义键盘快捷方式的详细信息，请参阅 Microsoft 文档中 Azure Data Studio 中的 [Keyboard 快捷方式](https://learn.microsoft.com/en-us/azure-data-studio/keyboard-shortcuts)。

</div>

<div class="ghd-tool xcode">

## 简介

本指南演示如何从 Xcode 中的 GitHub Copilot 获取编码建议。 要查看其他常用编码环境的说明，请使用页面顶部的工具切换器。

## Prerequisites

* ```
            **对 Copilot 的访问权限**。 要在 Xcode 中使用 GitHub Copilot，你需要通过 免费Copilot 获得有限访问权限，或者通过付费的 Copilot 计划获得完全访问权限。 请参阅“[AUTOTITLE](/copilot/about-gith

# C# Dev Kit for Visual Studio Code

This repository is where we (Microsoft) gather and interact with the community around the [C# Dev Kit extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csdevkit) for Visual Studio Code. To report an issue here, ideally you would use the 'Report an Issue' capability within VS Code which will log an issue in this repository for us to triage and keep updated.

## Contributing

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Triage

When triaging issues in this repo teams are expected to follow the [triage guidelines](TRIAGE.md).

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
*terminal.txt*   Nvim


                            NVIM REFERENCE MANUAL


Terminal emulator                                     *terminal* *terminal-emulator*

Nvim embeds a VT220/xterm terminal emulator based on libvterm. The terminal is
presented as a special 'buftype', asynchronously updated as data is received
from the connected program.

Terminal buffers behave like normal buffers, except:
- With 'modifiable', lines can be edited but not deleted.
- 'scrollback' controls how many lines are kept.
- Output is followed ("tailed") if cursor is on the last line.
- 'modified' is the default. You can set 'nomodified' to avoid a warning when
  closing the terminal buffer.
- 'bufhidden' defaults to "hide".

                                      Type |gO| to see the table of contents.

==============================================================================
Start                                                           *terminal-start*

There are several ways to create a terminal buffer:

- Run the |:terminal| command.
- Call |nvim_open_term()| or `jobstart(…, {'term': v:true})`.
- Edit a "term://" buffer. Examples: >vim
    :edit term://bash
    :vsplit term://top

<    Note: To open a "term://" buffer from an autocmd, the |autocmd-nested|
    modifier is required. >vim
        autocmd VimEnter * ++nested split term://sh
<    (This is only mentioned for reference; use |:terminal| instead.)

When the terminal starts, the buffer contents are updated and the buffer is
named in the form of `term://{cwd}//{pid}:{cmd}`. This naming scheme is used
by |:mksession| to restore a terminal buffer (by restarting the {cmd}).

The terminal environment is initialized as in |jobstart-env|.

==============================================================================
Input                                                           *terminal-input*

To send input, enter |Terminal-mode| with |i|, |I|, |a|, |A| or
|:startinsert|. In this mode all keys except <C-\> are sent to the underlying
program. If <C-\> is pressed, the next key is sent unless it is <C-N> or <C-O>.
Use <C-\><C-N> to return to normal mode. |CTRL-\_CTRL-N|
Use <C-\><C-O> to execute one normal mode command and then return to terminal
mode. *t_CTRL-\_CTRL-O*

Terminal-mode forces these local options:

- 'cursorlineopt' = number
- 'nocursorcolumn'
- 'scrolloff' = 0
- 'sidescrolloff' = 0

Terminal-mode has its own |:tnoremap| namespace for mappings, this can be used
to automate any terminal interaction.

To map <Esc> to exit terminal-mode: >vim
    :tnoremap <Esc> <C-\><C-n>

To simulate |i_CTRL-R| in terminal-mode: >vim
    :tnoremap <expr> <C-R> '<C-\><C-N>"'.nr2char(getchar()).'pi'

To use `ALT+{h,j,k,l}` to navigate windows from any mode: >vim
    :tnoremap <A-h> <C-\><C-N><C-w>h
    :tnoremap <A-j> <C-\><C-N><C-w>j
    :tnoremap <A-k> <C-\><C-N><C-w>k
    :tnoremap <A-l> <C-\><C-N><C-w>l
    :inoremap <A-h> <C-\><C-N><C-w>h
    :inoremap <A-j> <C-\><C-N><C-w>j
    :inoremap <A-k> <C-\><C-N><C-w>k
    :inoremap <A-l> <C-\><C-N><C-w>l
    :nnoremap <A-h> <C-w>h
    :nnoremap <A-j> <C-w>j
    :nnoremap <A-k> <C-w>k
    :nnoremap <A-l> <C-w>l

You can also create menus similar to terminal mode mappings, but you have to
use |:tlmenu| instead of |:tmenu|.

Mouse input has the following behavior:

- If the program has enabled mouse events, the corresponding events will be
  forwarded to the program.
- If mouse events are disabled (the default), terminal focus will be lost and
  the event will be processed as in a normal buffer.
- If another window is clicked, terminal focus will be lost and nvim will jump
  to the clicked window
- If the mouse wheel is used while the mouse is positioned in another window,
  the terminal won't lose focus and the hovered window will be scrolled.

==============================================================================
Configuration                                                  *terminal-config*

- Options: 'modified', 'scrollback'
- Events: |TermOpen|, |TermEnter|, |TermLeave|, |TermClose|
- Event groups: "nvim.terminal" |default-autocmds|
- Highlight groups: |hl-TermCursor|

Terminal sets local defaults for some options, which may differ from your
global configuration.

- 'list' is disabled
- 'wrap' is disabled
- 'number' is disabled
- 'relativenumber' is disabled
- 'signcolumn' is set to "no"
- 'foldcolumn' is set to "0"

You can change the defaults with a TermOpen autocommand: >vim
    :autocmd TermOpen * setlocal list

By default, "[Process exited]" is displayed when the terminal process ends. To
disable that, you can delete the "nvim.terminal" TermClose handler (this also
deletes other |default-autocmds| TermClose functionality): >vim
    :autocmd! nvim.terminal TermClose
<

TERMINAL COLORS ~

The `{g,b}:terminal_color_x` variables control the terminal color palette,
where `x` is the color index between 0 and 15 inclusive.  The variables are
read during |TermOpen|. The value must be a color name or hexadecimal string.
Example: >vim
    let g:terminal_color_4 = '#ff0000'
    let g:terminal_color_5 = 'green'
Only works for RGB UIs (see 'termguicolors'); for 256-color terminals the
color index is just forwarded.

Editor highlighting (|syntax-highlighting|, |highlight-groups|, etc.) has
higher precedence: it is applied after terminal colors are resolved.

------------------------------------------------------------------------------
EVENTS                                                        *terminal-events*

Applications running in a :terminal buffer can send requests, which Nvim
exposes via the |TermRequest| event.

OSC 7: change working directory                                *terminal-osc7*

Shells can emit the "OSC 7" sequence to announce when the current directory
(CWD) changed.

You can configure your shell init (e.g. ~/.bashrc) to emit OSC 7, or your
terminal may attempt to do it for you.

To configure bash to emit OSC 7: >bash
  function print_osc7() {
    printf '\033]7;file://%s\033\\' "$PWD"
  }
  PROMPT_COMMAND='print_osc7'

Having ensured that your shell emits OSC 7, you can now handle it in Nvim. The
following code will run :lcd whenever your shell CWD changes in a :terminal
buffer: >lua

  vim.api.nvim_create_autocmd({ 'TermRequest' }, {
    desc = 'Handles OSC 7 dir change requests',
    callback = function(ev)
      local val, n = string.gsub(ev.data.sequence, '\027]7;file://[^/]*', '')
      if n > 0 then
        -- OSC 7: dir-change
        local dir = val
        if vim.fn.isdirectory(dir) == 0 then
          vim.notify('invalid dir: '..dir)
          return
        end
        vim.b[ev.buf].osc7_dir = dir
        if vim.api.nvim_get_current_buf() == ev.buf then
          vim.cmd.lcd(dir)
        end
      end
    end
  })

To try it out, select the above code and source it with `:'<,'>lua`, then run
this command in a :terminal buffer: >

    printf "\033]7;file://./foo/bar\033\\"

OSC 52: write to system clipboard                             *terminal-osc52*

Applications in the :terminal buffer can write to the system clipboard by
emitting an OSC 52 sequence. Example: >

    printf '\033]52;;%s\033\\' "$(echo -n 'Hello world' | base64)"

Nvim uses the configured |clipboard| provider to write to the system
clipboard. Reading from the system clipboard with OSC 52 is not supported, as
this would allow any arbitrary program in the :terminal to read the user's
clipboard.

OSC 52 sequences sent from the :terminal buffer do not emit a |TermRequest|
event. The event is handled directly by Nvim and is not forwarded to plugins.

OSC 133: shell integration                    *terminal-osc133* *shell-prompt*

Shells can emit semantic escape sequences (OSC 133) to mark where each prompt
starts and ends. The start of a prompt is marked by sequence `OSC 133 ; A ST`,
and the end by `OSC 133 ; B ST`.

You can configure your shell init (e.g. ~/.bashrc) to emit OSC 133 sequences,
or your terminal may attempt to do it for you (assuming your shell config
doesn't interfere).

- fish: https://fishshell.com/docs/current/relnotes.html#improved-terminal-support
- kitty: https://sw.kovidgoyal.net/kitty/shell-integration/
- powershell: https://learn.microsoft.com/en-us/windows/terminal/tutorials/shell-integration#powershell-pwshexe
- vscode: https://code.visualstudio.com/docs/terminal/shell-integration

To configure bash to mark the start of each prompt, set $PROMPT_COMMAND: >bash

    # Prompt start:
    PROMPT_COMMAND='printf "\033]133;A\007"'
<
                                                *terminal_]]* *terminal_[[*
The |]]| and |[[| motions jump to the next/previous prompts, if your shell
emits OSC 133 as described above.

                                                *shell-prompt-signs*
To annotate each terminal prompt with a sign, call |nvim_buf_set_extmark()|
from a |TermRequest| handler: >lua

    vim.api.nvim_create_autocmd('TermOpen', {
      command = 'setlocal signcolumn=auto',
    })
    local ns = vim.api.nvim_create_namespace('my.terminal.prompt')
    vim.api.nvim_create_autocmd('TermRequest', {
      callback = function(ev)
        if string.match(ev.data.sequence, '^\027]133;A') then
          local lnum = ev.data.cursor[1]
          vim.api.nvim_buf_set_extmark(ev.buf, ns, lnum - 1, 0, {
            sign_text = '▶',
            sign_hl_group = 'SpecialChar',
          })
        end
      end,
    })
<
==============================================================================
Status Variables                                             *terminal-status*

Terminal buffers maintain some buffer-local variables and options. The values
are initialized before TermOpen, so you can use them in a local 'statusline'.
Example: >vim
    :autocmd TermOpen * setlocal statusline=%{b:term_title}

- *b:term_title*  Terminal title (user-writable), typically displayed in the
  window title or tab title of a graphical terminal emulator. Terminal
  programs can set this by emitting an escape sequence.
- 'channel'  Terminal PTY |job-id|.  Can be used with |chansend()| to send
  input to the terminal.
- The |TermClose| event gives the terminal job exit code in the |v:event|
  "status" field. For example, this autocommand outputs the terminal's exit
  code to |:messages|: >vim
    autocmd TermClose * echom 'Terminal exited with status '..v:event.status

Use |jobwait()| to check if the terminal job has finished: >vim
    let running = jobwait([&channel], 0)[0] == -1
<
==============================================================================
:Termdebug plugin                         *terminal-debug* *terminal-debugger*
                                               *package-termdebug* *termdebug*

The Terminal debugging plugin can be used to debug a program with gdb and view
the source code in a Vim window.  Since this is completely contained inside
Vim this also works remotely over an ssh connection.

Starting ~
                                                        *termdebug-starting*
Load the plugin with this command: >vim
    packadd termdebug
When loading the plugin from the |vimrc| file, add the "!" attribute: >vim
    packadd! termdebug
<                                                       *:Termdebug*
To start debugging use `:Termdebug` or `:TermdebugCommand` followed by the
command name, for example: >vim
    :Termdebug vim

This opens two windows:

- gdb window: A terminal window in which "gdb vim" is executed.  Here you can
  directly interact with gdb.
- program window: A terminal window for the executed program.  When "run" is
  used in gdb the program I/O will happen in this window, so that it does not
  interfere with controlling gdb.

The current window is used to show the source code.  When gdb pauses the
source file location will be displayed, if possible.  A sign is used to
highlight the current position, using highlight group debugPC.

If the buffer in the current window is modified, another window will be opened
to display the current gdb position.

Focus the terminal of the executed program to interact with it.  This works
the same as any command running in a terminal window.

When the debugger ends, typically by typing "quit" in the gdb window, the two
opened windows are closed.

Only one debugger can be active at a time.
                                                        *:TermdebugCommand*
If you want to give specific commands to the command being debugged, you can
use the `:TermdebugCommand` command followed by the command name and
additional parameters. >vim
    :TermdebugCommand vim --clean -c ':set nu'

Both the `:Termdebug` and `:TermdebugCommand` support an optional "!" bang
argument to start the command right away, without pausing at the gdb window
(and cursor will be in the debugged window).  For example: >vim
    :TermdebugCommand! vim --clean

To attach gdb to an already running executable or use a core file, pass extra
arguments.  E.g.: >vim
    :Termdebug vim core
    :Termdebug vim 98343

If no argument is given, you'll end up in a gdb window, in which you need to
specify which command to run using e.g. the gdb `file` command.


Example session ~
                                                        *termdebug-example*
Start in the Vim "src" directory and build Vim: >
    % make
Start Vim: >
    % ./vim
Load the termdebug plugin and start debugging Vim: >vim
    :packadd termdebug
    :Termdebug vim
You should now have three windows:
- source:  where you started
- gdb:     you can type gdb commands here
- program: the executed program will use this window

Put focus on the gdb window and type: >
    break ex_help
    run
Vim will start running in the program window.  Put focus there and type: >vim
    :help gui
Gdb will run into the ex_help breakpoint.  The source window now shows the
ex_cmds.c file.  A red "1 " marker will appear in the signcolumn where the
breakpoint was set.  The line where the debugger stopped is highlighted.  You
can now step through the program.  You will see the highlighting move as the
debugger executes a line of source code.

Run |:Over| a few times until the for loop is highlighted.  Put the cursor on
the end of "eap->arg", then call ":Eval".  You will see this displayed: >
    "eap->arg": 0x555555e68855 "gui"
This way you can inspect the value of local variables.  You can also focus the
gdb window and use a "print" command, e.g.: >
    print *eap
If mouse pointer movements are working, Vim will also show a balloon when the
mouse rests on text that can be evaluated by gdb.
You can also use the "K" mapping that will either use Nvim floating windows
to show the results.

Now go back to the source window and put the cursor on the first line after
the for loop, then type: >
    :Break
You will see a "1" marker appear, this indicates the new breakpoint.  Now
run ":Cont" command and the code until the breakpoint will be executed.

You can type more advanced commands in the gdb window.  For example, type: >
    watch curbuf
Now run ":Cont" (or type "cont" in the gdb window). Execution
will now continue until the value of "curbuf" changes, which is in do_ecmd().
To remove this watchpoint again type in the gdb window: >
    delete 3

You can see the stack by typing in the gdb window: >
    where
Move through the stack frames, e.g. with: >
    frame 3
The source window will show the code, at the point where the call was made to
a deeper level.


Stepping through code ~
                                                        *termdebug-stepping*
Put focus on the gdb window to type commands there.  Some common ones are:
- CTRL-C:   interrupt the program
- next:     execute the current line and stop at the next line
- step:     execute the current line and stop at the next statement,
            entering functions
- until:    execute until past the current cursor line or past a specified
            position or the current stack frame returns
- finish:   execute until leaving the current function
- where:    show the stack
- frame N:  go to the Nth stack frame
- continue: continue execution

                                                *:Run* *:Arguments*
In the window showing the source code these commands can be used to control
gdb:
- `:Run` [args]        run the program with [args] or the previous arguments
- `:Arguments` {args}  set arguments for the next `:Run`

- *:Break* set a breakpoint at the cursor position
- :Break [{position}] [thread {nr}] [if {expr}]
  set a breakpoint at the specified position if {position} is omitted, use the
  current file and line thread {nr} limits the breakpoint to one thread if
  {expr} sets a conditional breakpoint.
  Examples: >
      :Break if argc == 1
      :Break 42 thread 3 if x > 10
      :Break main
<
- *:Tbreak* set a temporary breakpoint at the cursor position
- :Tbreak [{position}] [thread {nr}] [if {expr}]
  like `:Break`, but the breakpoint is deleted after it is hit once.
  Examples: >
      :Tbreak if argc == 1
      :Tbreak 42 thread 3 if x > 10
      :Tbreak main
<
- *:Clear* delete the breakpoint at the cursor position
- *:ToggleBreak* set a breakpoint at the cursor position or delete all
               breakpoints at the cursor positoin

- *:Step*       execute the gdb "step" command
- *:Over*       execute the gdb "next" command (`:Next` is a Vim command)
- *:Until*      execute the gdb "until" command
- *:Finish*     execute the gdb "finish" command
- *:Continue*   execute the gdb "continue" command
- *:RunOrContinue* execute the gdb "continue" command if program is running,
                 otherwise run the program
- *:Stop*       interrupt the program

If gdb stops at a source line and there is no window currently showing the
source code, a new window will be created for the source code.  This also
happens if the buffer in the source code window has been modified and can't be
abandoned.

Gdb gives each breakpoint a number.  In Vim the number shows up in the sign
column, with a red background.  You can use these gdb commands:
- info break    list breakpoints
- delete N      delete breakpoint N
You can also use the `:Clear` command if the cursor is in the line with the
breakpoint, or use the "Clear breakpoint" right-click menu entry.


Inspecting variables ~
                                        *termdebug-variables* *:Evaluate*
- `:Evaluate`        evaluate the expression under the cursor
- `K`                same (see |termdebug_map_K| to disable)
- `:Evaluate` {expr} evaluate {expr}
- `:'<,'>Evaluate`   evaluate the Visually selected text

This is similar to using "print" in the gdb window.
You can usually shorten `:Evaluate` to `:Ev`.
The result is displayed in a floating window.
You can move the cursor to this window by running `:Evaluate` (or `K`) again.


Navigating stack frames ~
                                *termdebug-frames* *:Frame* *:Up* *:Down*
- `:Frame` [frame]       select frame [frame], which is a frame number,
                       address, or function name (default: current frame)
- `:Up` [count]          go up [count] frames (default: 1; the frame that
                       called the current)
- `+`                    same (see |termdebug_map_plus| to disable)
- `:Down` [count]        go down [count] frames (default: 1; the frame called
                       by the current)
- `-`                    same (see |termdebug_map_minus| to disable)


Other commands ~
                                                        *termdebug-commands*
- *:Gdb*      jump to the gdb window
- *:Program*  jump to the window with the running program
- *:Source*   jump to the window with the source code, create it if there
            isn't one
- *:Asm*      jump to the window with the disassembly, create it if there
            isn't one
- *:Var*      jump to the window with the local and argument variables,
            create it if there isn't one.  This window updates whenever the
            program is stopped

Events ~
                                                        *termdebu
# /etc/nginx/nginx.conf
# GUBON OS V5 主配置上下文

user nginx;
worker_processes auto;
pid /run/nginx.pid;

events {
    worker_connections 1024;
}

http {
    # --------------------------------------------------------
    # 核心上下文區域：在這裡引入剛才的 Cloudflare 種子設定
    # --------------------------------------------------------
    include /etc/nginx/cloudflare/cloudflare_ips.conf;

    # 基礎傳輸優化
    sendfile            on;
    tcp_nopush          on;
    tcp_nodelay         on;
    keepalive_timeout   65;
    types_hash_max_size 4096;

    include             /etc/nginx/mime.types;
    default_type        application/octet-stream;

    # 日誌格式：這時候 $realip_remote_addr 就會拿到真正的訪客 IP
    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;
    error_log   /var/log/nginx/error.log warn;

    # 你的虛擬主機設定
    include /etc/nginx/conf.d/*.conf;
}
