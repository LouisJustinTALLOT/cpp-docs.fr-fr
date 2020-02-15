---
title: /ERRORREPORT (dumpbin.exe)
description: Référence de l’option de ligne de commande Microsoft DUMPBIN Utility/ERRORREPORT.
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
helpviewer_keywords:
- -ERRORREPORT dumpbin option
- ERRORREPORT dumpbin option
- /ERRORREPORT dumpbin option
ms.assetid: 51178c43-4f95-4fda-8f97-50a257d1c948
ms.openlocfilehash: 665b4b1e7c01de4a1fcd848a9e6b36ddbf2944c9
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257674"
---
# <a name="errorreport-dumpbinexe"></a>/ERRORREPORT (dumpbin.exe)

> [!NOTE]
> L’option/ERRORREPORT est déconseillée. À compter de Windows Vista, le rapport d’erreurs est contrôlé par les paramètres d' [rapport d’erreurs Windows (WER)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Syntaxe

> **/Errorreport**\[**aucune** \| **invite** de \| de **file d’attente** \| **Envoyer** ]

## <a name="remarks"></a>Notes

Les arguments **/errorreport** sont remplacés par les paramètres de service rapport d’erreurs Windows. DUMPBIN envoie automatiquement des rapports d’erreurs internes à Microsoft, si la création de rapports est activée par Rapport d’erreurs Windows. Aucun rapport n’est envoyé s’il est désactivé par Rapport d’erreurs Windows.

## <a name="see-also"></a>Voir aussi

[DUMPBIN, options](dumpbin-options.md)
