---
description: 'En savoir plus sur : Register Storage-Class specifier'
title: Spécificateur register de classe de stockage
ms.date: 11/04/2016
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
ms.openlocfilehash: a7e062f72191f6ee6d678d18b902ea184d362714
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120755"
---
# <a name="register-storage-class-specifier"></a>Spécificateur register de classe de stockage

**Spécifique à Microsoft**

Le compilateur Microsoft C/C++ n'honore pas les requêtes utilisateur pour les variables de registre. Toutefois, pour la portabilité, toutes les autres sémantiques associées au **`register`** mot clé sont honorées par le compilateur. Par exemple, vous ne pouvez pas appliquer l’opérateur unaire Address-of ( **&** ) à un objet Register et le mot clé ne peut pas **`register`** être utilisé sur les tableaux.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Spécificateurs de classe de stockage pour les déclarations de Internal-Level](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
