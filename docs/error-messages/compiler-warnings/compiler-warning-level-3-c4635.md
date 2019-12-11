---
title: Avertissement du compilateur (niveau 3) C4635
ms.date: 11/04/2016
f1_keywords:
- C4635
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
ms.openlocfilehash: fd3bf6c1b14c6dae8e2fa95a54e2d4fbc4f295c5
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991850"
---
# <a name="compiler-warning-level-3-c4635"></a>Avertissement du compilateur (niveau 3) C4635

Cible de commentaire de document XML : code XML incorrect : raison

Le compilateur a détecté un problème avec les balises XML.  Corrigez le problème et recompilez.

L’exemple suivant génère l’avertissement C4635 :

```cpp
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

Le problème avec cet exemple est que la balise de fin de \<Résumé > est mal formée et que le compilateur ne la reconnaît pas comme balise de fin de > de \<.  La balise de > de membre \<est incorporée dans le fichier. XDC par le compilateur dans chaque compilation/doc.  Le problème ici est que la balise de fin \</Member > ne correspond pas à la balise de début précédente traitée par le compilateur (\<Résumé >.
