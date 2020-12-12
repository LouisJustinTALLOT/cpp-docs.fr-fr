---
description: 'En savoir plus sur : instanciation de modèle de fonction'
title: Instanciation du modèle de fonction
ms.date: 11/04/2016
helpviewer_keywords:
- templates, instantiation
- function templates, instantiation
- instantiation, function templates
ms.assetid: f22a07c7-3ad1-465a-84f5-8737e274bd47
ms.openlocfilehash: 1278190c9f86034374ee295a308fe0b8396b8716
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341371"
---
# <a name="function-template-instantiation"></a>Instanciation du modèle de fonction

Lorsqu'un modèle de fonction est appelé pour la première fois pour chaque type, le compilateur crée une instanciation. Chaque instanciation est une version de la fonction basée sur un modèle spécialisée pour le type. Cette instanciation est appelée chaque fois que la fonction est utilisée pour le type. Si vous avez plusieurs instanciations identiques, même dans différents modules, une seule copie de l'instanciation finira dans le fichier exécutable.

La conversion des arguments de fonction est autorisée dans les modèles de fonction pour toute paire argument-paramètre où le paramètre ne dépend pas d’un argument template.

Les modèles de fonction peuvent être instanciés de manière explicite en déclarant le modèle avec un type particulier comme argument. Par exemple, le code suivant est autorisé :

```cpp
// function_template_instantiation.cpp
template<class T> void f(T) { }

// Instantiate f with the explicitly specified template.
// argument 'int'
//
template void f<int> (int);

// Instantiate f with the deduced template argument 'char'.
template void f(char);
int main()
{
}
```

## <a name="see-also"></a>Voir aussi

[Modèles de fonction](../cpp/function-templates.md)
