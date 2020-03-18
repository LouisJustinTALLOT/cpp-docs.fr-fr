---
title: /ERRORREPORT (dumpbin.exe)
description: Référence de l’option de ligne de commande Microsoft DUMPBIN Utility/ERRORREPORT.
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT_dumpbin
helpviewer_keywords:
- -ERRORREPORT dumpbin option
- ERRORREPORT dumpbin option
- /ERRORREPORT dumpbin option
ms.assetid: 51178c43-4f95-4fda-8f97-50a257d1c948
ms.openlocfilehash: f701c2e28dcf82194589877709bf6959de4bcbfc
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439936"
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
