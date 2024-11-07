# Mermaid
sequenceDiagram
actor s as 学生
actor r as 医師
actor z as 事務局
actor t as 教員

participant db as 出席データベース

s ->>+ r : 診断発行の依頼
r -->>- s : 診断書の発行
s -->> z : 診断書を提出
s -->> z : 発熱報告書を提出

z ->>+ s : 確認書の発行

loop 影響する教員
    z ->> t : 病欠を通知
    alt 病欠を認める
        t ->> db : 病欠登録
    end
end
