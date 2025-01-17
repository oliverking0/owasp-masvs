# V2: Требования к конфиденциальности и хранению данных

## Цель проверки

Защита чувствительных данных, таких, как данные пользователя для авторизации (логин + пароль) и персональные данные, является ключевым аспектом в безопасности мобильных приложений. Во-первых, чувствительные данные могут  быть непреднамеренно раскрыты другим приложениям, работающим на том же устройстве, если механизмы операционной системы, такие как межпроцессное взаимодействие (IPC), используются ненадлежащим образом. Данные также могут непреднамеренно попасть в облачное хранилище, резервную копию или кеш клавиатуры. Кроме того, мобильные устройства могут быть потеряны или украдены легче чем другие типы устройств, поэтому злоумышленник, получивший физический доступ к устройству, является наиболее вероятным сценарием. В этом случае могут быть реализованы дополнительные меры защиты для затруднения извлечения чувствительных данных с устройства.

Следует обратить внимание, что MASVS ориентирован на приложения, и потому не охватывает политики безопасности на уровне устройства (MDM - Mobile Device Managment). Мы поощряем использование таких политик в контексте предприятия для повышения безопасности данных.

### Определение чувствительных данных

К чувствительным данным в контексте MASVS относятся как данные пользователя для авторизации, так и любые другие данные, которые считаются чувствительными в конкретном контексте, например:

- Персональные данные, которые могут быть использованы для кражи личности: номера социального страхования, кредитных карт, банковских счетов, информация о здоровье.
- Конфиденциальная информация, которая может привести к репутационному ущербу и/или финансовым потерям, если она скомпрометирована: информация о договорах, информация, охватываемая соглашениями о неразглашении, управленческая информация;
- Любые данные, которые должны быть защищены по закону или внутренним требованиям компании.

## Требования безопасности

Подавляющее большинство проблем с раскрытием информации можно предотвратить, следуя простым правилам. Большинство требований, перечисленных в этой главе, являются обязательными для всех уровней проверки.

| # | MSTG-ID | Описание | L1 | L2 |
| -- | ---------- | ---------------------- | - | - |
| **2.1** | MSTG-STORAGE-1 | Хранилище учетных данных системы должно использоваться надлежащим образом для хранения чувствительных данных, таких как персональные данные, данные пользователя для авторизации и криптографические ключи. | x | x |
| **2.2** | MSTG-STORAGE-2 | Чувствительные данные хранятся только во внутреннем хранилище приложения, либо в системном хранилище авторизационных данных. | x | x |
| **2.3** | MSTG-STORAGE-3 | Чувствительные данные не попадают в логи приложения. | x | x |
| **2.4** | MSTG-STORAGE-4 | Никакие чувствительные данные не передаются третьей стороне, если это не является необходимой частью архитектуры. | x | x |
| **2.5** | MSTG-STORAGE-5 | Кэш клавиатуры выключен для полей ввода чувствительных данных. | x | x |
| **2.6** | MSTG-STORAGE-6 | Чувствительные данные недоступны для механизмов межпроцессного взаимодействия (IPC). | x | x |
| **2.7** | MSTG-STORAGE-7 | Никакие чувствительные данные, такие как пароли или пин-коды, не видны через пользовательский интерфейс. | x | x |
| **2.8** | MSTG-STORAGE-8 | Никакие чувствительные данные не попадают в бэкапы, создаваемые операционной системой. |   | x |
| **2.9** | MSTG-STORAGE-9 | Приложение скрывает чувствительные данные с экрана, когда находится в фоновом режиме. |  | x |
| **2.10** | MSTG-STORAGE-10 | Приложение не хранит чувствительные данные в памяти дольше, чем необходимо, и полностью удаляет их из памяти после работы с ними. |  | x |
| **2.11** | MSTG-STORAGE-11 | Приложение требует от пользователя минимальную настройку доступа к устройству, такую, как установку пин-кода на устройство. |  | x |
| **2.12** | MSTG-STORAGE-12 | Приложение информирует пользователя о персональных данных, которые оно обрабатывает, а также о лучших практиках безопасности, которым должен следовать пользователь при использовании приложения. | x | x |
| **2.13** | MSTG-STORAGE-13 | Конфиденциальные данные локально не должны храниться на мобильном устройстве. Вместо этого необходимые данные должны получаться с сервера и храниться только в памяти. |  | x |
| **2.14** | MSTG-STORAGE-14 | Если конфиденциальные данные все же требуется хранить локально, они должны быть зашифрованы с помощью ключа, полученного из аппаратного хранилища, которое требует проверки подлинности. |  | x |
| **2.15** | MSTG-STORAGE-15 | Локальное хранилище приложения должно быть стерто после превышения допустимого количества неудачных попыток. |  | x |

## Ссылки

OWASP MSTG содержит подробные инструкции по верификации требований, перечисленных в этом разделе.

- Android: Тестирование хранения данных - <https://github.com/OWASP/owasp-mstg/blob/master/Document/0x05d-Testing-Data-Storage.md>
- iOS: Тестирование хранения данных - <https://github.com/OWASP/owasp-mstg/blob/master/Document/0x06d-Testing-Data-Storage.md>

Для получения дополнительной информации смотрите также:

- OWASP Mobile Top 10: M1 (Improper Platform Usage) - <https://owasp.org/www-project-mobile-top-10/2016-risks/m1-improper-platform-usage>
- OWASP Mobile Top 10: M2 (Insecure Data Storage) - <https://owasp.org/www-project-mobile-top-10/2016-risks/m2-insecure-data-storage>
- CWE 117 (Improper Output Neutralization for Logs) - <https://cwe.mitre.org/data/definitions/117.html>
- CWE 200 (Information Exposure) - <https://cwe.mitre.org/data/definitions/200.html>
- CWE 276 (Incorrect Default Permissions) - <https://cwe.mitre.org/data/definitions/276.html>
- CWE 311 (Missing Encryption of Sensitive Data) - <https://cwe.mitre.org/data/definitions/311.html>
- CWE 312 (Cleartext Storage of Sensitive Information) - <https://cwe.mitre.org/data/definitions/312.html>
- CWE 316 (Cleartext Storage of Sensitive Information in Memory) - <https://cwe.mitre.org/data/definitions/316.html>
- CWE 359 (Exposure of Private Information ('Privacy Violation')) - <https://cwe.mitre.org/data/definitions/359.html>
- CWE 522 (Insufficiently Protected Credentials) - <https://cwe.mitre.org/data/definitions/522.html>
- CWE 524 (Information Exposure Through Caching) - <https://cwe.mitre.org/data/definitions/524.html>
- CWE 530 (Exposure of Backup File to an Unauthorized Control Sphere) - <https://cwe.mitre.org/data/definitions/530.html>
- CWE 532 (Information Exposure Through Log Files) - <https://cwe.mitre.org/data/definitions/532.html>
- CWE 534 (Information Exposure Through Debug Log Files) - <https://cwe.mitre.org/data/definitions/534.html>
- CWE 634 (Weaknesses that Affect System Processes) - <https://cwe.mitre.org/data/definitions/634.html>
- CWE 798 (Use of Hard-coded Credentials) - <https://cwe.mitre.org/data/definitions/798.html>
- CWE 921 (Storage of Sensitive Data in a Mechanism without Access Control) - <https://cwe.mitre.org/data/definitions/921.html>
- CWE 922 (Insecure Storage of Sensitive Information) - <https://cwe.mitre.org/data/definitions/922.html>
