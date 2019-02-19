---
title: Spécificateur register de classe de stockage
ms.date: 11/04/2016
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
ms.openlocfilehash: 0fac6db2254a909d0ec558a7e76f7ccf32aa7ac3
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147345"
---
# <a name="register-storage-class-specifier"></a>Spécificateur register de classe de stockage

**Section spécifique à Microsoft**

Le compilateur Microsoft C/C++ n'honore pas les requêtes utilisateur pour les variables de registre. Toutefois, pour la portabilité, toutes les autres sémantiques associées au mot clé **register** sont honorées par le compilateur. Par exemple, vous ne pouvez pas appliquer l'opérateur unaire address-of (**&**) pour enregistrer un objet. De la même manière, le mot clé **register** ne peut pas être utilisé sur les tableaux.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Spécificateurs de classe de stockage pour les déclarations de niveau interne](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
