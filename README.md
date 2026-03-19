<p align="center">
    <a href="https://www.xcoorp.com" target="_blank">
        <img src="https://www.xcoorp.com/wp-content/uploads/2021/05/logo_xcoorp_340-300x56.png" width="400" alt="XCoorp Logo">
    </a>
</p>

# 📦 Archiviertes Projekt:

> **Hinweis:** Dieses Projekt wurde **archiviert** und ist nicht mehr aktiv in Entwicklung oder Betrieb.  
> Es wird ausschließlich zu **Nachweiszwecken** gemäß **ISO/IEC 27001** aufbewahrt.

---

## 🔖 Projektdetails

| Attribut | Beschreibung |
|----------|--------------|
| **Archivierungsdatum** | 19.03.2026  |
| **Status** | Archiviert |
| **Verantwortlich** | [Tobias Oitzinger](https://github.com/toitzi)/ Softwareentwicklung |
| **Kontakt** | support@xcoorp.com |
| **Letzte Aktivität** | 26.06.2024 |
| **Archiviert durch** | [Michael Peck](https://github.com/mikexcoorp) / Geschäftsleitung |

---

## 📚 Zweck der Archivierung

Dieses Repository wurde archiviert im Rahmen des Informationssicherheitsmanagementsystems (ISMS) nach **ISO/IEC 27001**, um die folgenden Anforderungen zu erfüllen:

- **A.5.36**: Aufbewahrung und Entsorgung von Informationen
- **A.7.12**: Klassifikation von Informationen
- **A.8.10**: Protokollierung von Aktivitäten (falls relevant)
- **A.8.11**: Überwachung (falls Logs enthalten sind)

---

## 🔐 Informationsklassifikation

| Kriterium | Bewertung |
|----------|-----------|
| **Vertraulichkeit** | ☐ Öffentlich ☑ Interner Gebrauch ☐ Eingeschränkt |


---

## 🗃 Aufbewahrungsfrist

| Kriterium | Wert |
|----------|------|
| **Beginn der Frist** | 19.03.2026 |
| **Dauer** | 3 Jahre |
| **Löschdatum** |  19.03.2029 |
| **Löschverantwortlicher** | [Markus Lang](https://github.com/markwien) / Geschäftsleitung  |

---

## 🛑 Einschränkungen

- Dieses Repository ist **read-only**.
- Pull Requests oder Issues werden **nicht** mehr bearbeitet.
- Nutzung auf eigene Verantwortung, keine Sicherheitsupdates mehr.

---

## ✅ ISO 27001 Verknüpfung

Dieses Projekt ist Teil des ISO/IEC 27001 Asset Registers und dient als **Nachweisobjekt** für Audits und Reviews.

---

> Bei Fragen zur Archivierung oder zur Nutzung im Rahmen von Audits bitte an **Markus Lang mark@xcoorp.com** wenden.




<p align="center">
<a href="LICENSE"><img alt="Software License" src="https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square"></a>
<a href="composer.json"><img alt="Laravel Version Requirements" src="https://img.shields.io/badge/laravel-~10.0-gray?logo=laravel&style=flat-square&labelColor=F05340&logoColor=white"></a>
</p>

<h1>Novu - Laravel Notification Channel</h1>

This package makes it easy to send notifications using [Novu](https://novu.co)
````php
class InvoicePaidNotification extends Notification
{
    // Trigger a specific notification event
    public function toNovuEvent($notifiable)
    {
        return NovuMessage::create('workflow_1234')
            ->addVariable('invoice_id', $this->invoice->id)
            ->toSubscriberId('123456789');
    }
}
````
## Contents

- [Installation](#installation)
- [Usage](#usage)
- [API Overview](#novu-message)
    - [Novu Message](#novu-message)
- [Testing](#testing)
- [License](#license)


## Installation

The Novu notification channel can be installed easily via Composer:

````bash
$ composer require xcoorp/laravel-novu-notifications
````

## Usage

In order to send a notification via the Novu channel, you'll need to specify the channel in the `via()` method of your notification:

````php
use NotificationChannels\Novu\NovuChannel;

public function via($notifiable)
{
    return [
        NovuChannel::class
    ]
}
````

## API Overview

### Novu Message

Namespace: `NotificationChannels\Novu\NovuMessage`

The `NovuMessage` class encompasses an entire message that will be sent to the Novu API.

- `static create(?string $workflowId)` Instantiates and returns a new `NovuMessage` instance, optionally pre-configuring it with the workflow id
- `workflowId(string $workflowId)` Set the `workflowId` of the message (Your novu workflow trigger id)
- `to(array $to)` Array of recipient information like `subscriberId`, `phone`, etc...
- `toSubscriber(string $subscriberId)` Set the `subscriberId` of the recipient
- `variables(array $variables)` Set the variables (`payload`) of the message. Those are your novu event variables
- `addVariable(string $key, $value)` Add a single variable to the message
- `toArray()` Returns the data that will be sent to the Novu API as an array

## Testing

Functionality of this package is tested with [Pest PHP](https://pestphp.com/).
You can run the tests with:

``` bash
composer test
```

## Code of Conduct

In order to ensure that the community is welcoming to all, please review and abide by
the [Code of Conduct](CODE_OF_CONDUCT.md).

## Security Vulnerabilities

Please review the [security policy](SECURITY.md) on how to report security vulnerabilities.

## License

The MIT License (MIT). Please see [License File](LICENSE) for more information.
