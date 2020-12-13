---
description: 'En savoir plus sur : _except_handler3'
title: _except_handler3
ms.date: 11/04/2016
api_name:
- _except_handler3
api_location:
- msvcrt.dll
- msvcr90.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- msvcr110.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _except_handler3
- except_handler3
helpviewer_keywords:
- _except_handler3 function
- except_handler3 function
ms.assetid: b0c64898-0ae5-48b7-9724-80135a0813e2
ms.openlocfilehash: c6253152559516ea7162f887618df0bcbb4bc8ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331131"
---
# <a name="_except_handler3"></a>_except_handler3

Fonction CRT interne. Utilisée par une infrastructure pour rechercher le gestionnaire d'exceptions approprié pour traiter l'exception actuelle.

## <a name="syntax"></a>Syntaxe

```
int _except_handler3(
   PEXCEPTION_RECORD exception_record,
   PEXCEPTION_REGISTRATION registration,
   PCONTEXT context,
   PEXCEPTION_REGISTRATION dispatcher
);
```

#### <a name="parameters"></a>Paramètres

*exception_record*<br/>
[in] Informations sur l’exception spécifique.

*abonnement*<br/>
[in] Enregistrement qui indique la table d’étendue qui doit être utilisée pour rechercher le gestionnaire d’exceptions.

*context*<br/>
[in] Réservée.

*répartiteur*<br/>
[in] Réservée.

## <a name="return-value"></a>Valeur renvoyée

Si une exception doit être écartée, retourne `DISPOSITION_DISMISS`. Si l'exception doit être montée d'un niveau aux gestionnaires d'exceptions d'encapsulation, retourne `DISPOSITION_CONTINUE_SEARCH`.

## <a name="remarks"></a>Notes

Si cette méthode trouve un gestionnaire d'exceptions approprié, l'exception est passée au gestionnaire. Dans ce cas, cette méthode ne retourne pas au code qui l'a appelée et la valeur de retour est inutile.

## <a name="see-also"></a>Voir aussi

[Référence de fonction alphabétique](../c-runtime-library/reference/crt-alphabetical-function-reference.md)
