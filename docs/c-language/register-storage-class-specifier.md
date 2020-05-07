---
title: Spécificateur register de classe de stockage
ms.date: 11/04/2016
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
ms.openlocfilehash: 0fac6db2254a909d0ec558a7e76f7ccf32aa7ac3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325245"
---
# <a name="register-storage-class-specifier"></a>Spécificateur register de classe de stockage

**Spécifique à Microsoft**

Le compilateur Microsoft C/C++ n'honore pas les requêtes utilisateur pour les variables de registre. Toutefois, pour la portabilité, toutes les autres sémantiques associées au mot clé **register** sont honorées par le compilateur. Par exemple, vous ne pouvez pas appliquer l’opérateur unaire address**&**-of () à un objet Register et le mot clé **Register** ne peut pas être utilisé sur les tableaux.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Spécificateurs de classe de stockage pour les déclarations de niveau interne](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
