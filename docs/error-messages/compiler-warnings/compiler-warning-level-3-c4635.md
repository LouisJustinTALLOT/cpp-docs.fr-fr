---
description: 'En savoir plus sur : avertissement du compilateur (niveau 3) C4635'
title: Avertissement du compilateur (niveau 3) C4635
ms.date: 11/04/2016
f1_keywords:
- C4635
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
ms.openlocfilehash: e885c501e4f10719618bb552c153dc13a481332d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97168330"
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

Le problème avec cet exemple est que la balise de fin pour \<summary> est mal formée et que le compilateur ne la reconnaît pas comme \<summary> balise de fin.  La \<member> balise est incorporée dans le fichier. XDC par le compilateur dans chaque compilation/doc.  Le problème ici est que la balise de fin \</member> ne correspond pas à la balise de début précédente traitée par le compilateur ( \<summary> .
