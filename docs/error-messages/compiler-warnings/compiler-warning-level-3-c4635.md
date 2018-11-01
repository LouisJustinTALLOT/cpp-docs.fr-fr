---
title: Avertissement du compilateur (niveau 3) C4635
ms.date: 11/04/2016
f1_keywords:
- C4635
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
ms.openlocfilehash: 21873a883b19924ce3ef41511d65f8ae640875f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479233"
---
# <a name="compiler-warning-level-3-c4635"></a>Avertissement du compilateur (niveau 3) C4635

Cible de commentaire de document XML : code XML incorrect : raison

Le compilateur a détecté un problème avec les balises XML.  Corrigez le problème et recompilez.

L’exemple suivant génère l’avertissement C4635 :

```
// C4635.cpp
// compile with: /doc /clr /W3 /c
/// <summary>
/// The contents of the folder have changed.
/// <summary/>   // C4635

// try the following line instead
// /// </summary>
public ref class Test {};
```

Notez que la sortie de cet exemple indique : **La balise de fin 'member' ne correspond pas à la balise de début 'summary'.**

Le problème avec cet exemple est que la balise de fin pour \<Résumé > est mal formée, et le compilateur ne reconnaît pas en tant que le \<Résumé > balise de fin.  Le \<membre > est incorporée dans le fichier .xdc par le compilateur dans chaque compilation /doc.  Par conséquent, le problème ici est que la balise de fin \</Member >, ne correspond pas à la balise de début précédente que le compilateur traité (\<Résumé >.