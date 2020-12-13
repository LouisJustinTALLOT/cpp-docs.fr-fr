---
description: 'En savoir plus sur : ML d’erreur irrécupérable A1011'
title: Erreur ML irrécupérable A1011
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1011
helpviewer_keywords:
- A1011
ms.assetid: 7fbf092d-4189-4330-a884-dfa2268fc3dd
ms.openlocfilehash: 294ca2cbf512948514317589628969a3e63e71af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97129491"
---
# <a name="ml-fatal-error-a1011"></a>Erreur ML irrécupérable A1011

**la directive doit être dans un bloc de contrôle**

L’assembleur a trouvé une directive de niveau supérieur où l’un n’était pas attendu. Une des directives suivantes a été trouvée :

- [. SINON](dot-else.md) [, sans. Si](dot-if.md)

- [. ENDIF](dot-endif.md) sans [. Si](dot-if.md)

- [. ENDW](dot-endw.md) sans [. PENDANT](dot-while.md)

- [. UNTILCXZ](dot-untilcxz.md) sans [. RÉPÉTER](dot-repeat.md)

- [. CONTINUER](dot-continue.md) sans [. WHILe](dot-while.md) ou [. RÉPÉTER](dot-repeat.md)

- [. ARRÊTER](dot-break.md) sans [. WHILe](dot-while.md) ou [. RÉPÉTER](dot-repeat.md)

- [. SINON](dot-else.md) , suivant `.ELSE`

## <a name="see-also"></a>Voir aussi

[Messages d'erreur ML](ml-error-messages.md)
