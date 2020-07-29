---
title: Spécificateur register de classe de stockage
ms.date: 11/04/2016
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
ms.openlocfilehash: 513213222ee2c598455709a0891977a0949c8555
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229556"
---
# <a name="register-storage-class-specifier"></a>Spécificateur register de classe de stockage

**Spécifique à Microsoft**

Le compilateur Microsoft C/C++ n'honore pas les requêtes utilisateur pour les variables de registre. Toutefois, pour la portabilité, toutes les autres sémantiques associées au **`register`** mot clé sont honorées par le compilateur. Par exemple, vous ne pouvez pas appliquer l’opérateur unaire Address-of ( **&** ) à un objet Register et le mot clé ne peut pas **`register`** être utilisé sur les tableaux.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Spécificateurs de classe de stockage pour les déclarations de niveau interne](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
