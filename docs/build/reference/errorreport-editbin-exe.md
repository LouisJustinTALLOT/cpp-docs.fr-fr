---
title: /ERRORREPORT (editbin.exe)
description: Référence de l’option de ligne de commande Microsoft EDITBIN Utility/ERRORREPORT.
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
helpviewer_keywords:
- -ERRORREPORT editbin option
- ERRORREPORT editbin option
- /ERRORREPORT editbin option
ms.assetid: eca66ac3-b754-4bd7-9dd4-e04fc79a71b6
ms.openlocfilehash: 6c2ec8b6cda7b794114ed38cfb72b885bf2e38a1
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257590"
---
# <a name="errorreport-editbinexe"></a>/ERRORREPORT (editbin.exe)

> [!NOTE]
> L’option/ERRORREPORT est déconseillée. À compter de Windows Vista, le rapport d’erreurs est contrôlé par les paramètres d' [rapport d’erreurs Windows (WER)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Syntaxe

> **/Errorreport** \[ **aucune** \| **invite** de \| de **file d’attente** \| **Envoyer** ]

## <a name="remarks"></a>Notes

Les arguments **/errorreport** sont remplacés par les paramètres de service rapport d’erreurs Windows. EDITBIN envoie automatiquement des rapports d’erreurs internes à Microsoft, si la création de rapports est activée par Rapport d’erreurs Windows. Aucun rapport n’est envoyé s’il est désactivé par Rapport d’erreurs Windows.

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)
