---
description: 'En savoir plus sur : sécurité des threads dans la bibliothèque C++ standard'
title: Sécurité des threads dans la bibliothèque standard C++
ms.date: 11/04/2016
helpviewer_keywords:
- thread safety
- C++ Standard Library, thread safety
- thread safety, C++ Standard Library
ms.assetid: 9351c8fb-4539-4728-b0e9-226e2ac4284b
ms.openlocfilehash: ff5d8960b2fc8a79acbfb4fc1d0be508865714e9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289632"
---
# <a name="thread-safety-in-the-c-standard-library"></a>Sécurité des threads dans la bibliothèque standard C++

Les règles de sécurité des threads suivantes s’appliquent à toutes les classes de la bibliothèque standard C++, y compris `shared_ptr`, comme décrit ci-dessous.  Des garanties plus fortes sont parfois fournies, par exemple les objets iostream standard, comme décrit ci-dessous, et les types spécifiquement destinés au multithreading, comme ceux de [\<atomic>](../standard-library/atomic.md) .

Un objet est thread-safe pour la lecture à partir de plusieurs threads. Par exemple, étant donné un objet A, la lecture de A à partir du thread 1 et du thread 2 simultanément est sécurisée.

Si un thread écrit dans un objet, toutes les lectures et écritures dans cet objet sur le même thread ou d'autres threads doivent être protégées. Par exemple, étant donné un objet A, si le thread 1 écrit dans A, le thread 2 doit être dans l'impossibilité d'écrire ou de lire dans A.

La lecture et l'écriture dans une instance d'un type sont sécurisées, même si un autre thread lit ou écrit dans une autre instance du même type. Par exemple, étant donné des objets A et B du même type, l'opération est sécurisée quand A est écrit dans le thread 1 et que B est lu dans le thread 2.

## <a name="shared_ptr"></a>shared_ptr

Plusieurs threads peuvent lire et écrire simultanément différents objets [shared_ptr](../standard-library/shared-ptr-class.md), même quand ces objets sont des copies qui partagent la propriété.

## <a name="iostream"></a>iostream

Les objets iostream standard `cin`, `cout`, `cerr`, `clog`, `wcin`, `wcout`, `wcerr` et `wclog` suivent les mêmes règles que les autres classes, à cette exception près : l'écriture dans un objet à partir de plusieurs threads est sécurisée. Par exemple, le thread 1 peut écrire dans [cout](../standard-library/iostream.md#cout) en même temps que le thread 2. Toutefois, les sorties des deux threads peuvent alors être mélangées.

> [!NOTE]
> La lecture à partir d'une mémoire tampon de flux n'est pas considérée comme étant une opération de lecture. Elle est plutôt considérée comme une opération d'écriture, car l'état de la classe est modifié.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)
