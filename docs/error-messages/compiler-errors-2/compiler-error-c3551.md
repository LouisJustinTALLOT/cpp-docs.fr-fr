---
description: 'En savoir plus sur : erreur du compilateur C3551'
title: Erreur du compilateur C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: 813d483b696d0829f05108a35e5731f93f6004ea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223267"
---
# <a name="compiler-error-c3551"></a>Erreur du compilateur C3551

« type de retour spécifié à la fin attendu »

Si vous utilisez le **`auto`** mot clé en tant qu’espace réservé pour le type de retour d’une fonction, vous devez fournir un type de retour spécifié à la fin. Dans l’exemple suivant, le type de retour spécifié à la fin de la fonction `myFunction` est un pointeur vers un tableau de quatre éléments de type **`int`** .

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>Voir aussi

[Auto](../../cpp/auto-cpp.md)
