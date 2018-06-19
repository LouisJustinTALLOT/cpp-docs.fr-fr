---
title: Spécificateur register de classe de stockage │ Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- register variables
- register storage class
ms.assetid: 7577bf48-88ec-4191-873c-ef4217a4034e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 211f623923286e598f495920bcbdac3a9321b13a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32384598"
---
# <a name="register-storage-class-specifier"></a>Spécificateur register de classe de stockage
**Section spécifique à Microsoft**  
  
 Le compilateur Microsoft C/C++ n'honore pas les requêtes utilisateur pour les variables de registre. Toutefois, pour la portabilité, toutes les autres sémantiques associées au mot clé **register** sont honorées par le compilateur. Par exemple, vous ne pouvez pas appliquer l'opérateur unaire address-of (**&**) pour enregistrer un objet. De la même manière, le mot clé **register** ne peut pas être utilisé sur les tableaux.  
  
 **FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Spécificateurs de classe de stockage pour les déclarations de niveau interne](../c-language/storage-class-specifiers-for-internal-level-declarations.md)