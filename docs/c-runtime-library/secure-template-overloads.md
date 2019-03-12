---
title: Sécuriser les surcharges de modèle
ms.date: 11/04/2016
f1_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
helpviewer_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
- secure template overloads
ms.assetid: 562741d0-39c0-485e-8529-73d740f29f8f
ms.openlocfilehash: dfb13d5a48376efb72a845e2f5e2380407937f5b
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744565"
---
# <a name="secure-template-overloads"></a>Sécuriser les surcharges de modèle

Microsoft a déprécié de nombreuses fonctions de bibliothèque Runtime C (CRT) au profit de versions plus sécurisées. Par exemple, `strcpy_s` est le remplacement le plus sécurisé pour `strcpy`. Les fonctions dépréciées sont des sources courantes de bogues de sécurité, car elles n’empêchent pas les opérations qui peuvent écraser la mémoire. Par défaut, le compilateur génère un avertissement de dépréciation quand vous utilisez l’une de ces fonctions. Le CRT fournit des surcharges de modèle C++ pour ces fonctions afin de faciliter la transition vers des variantes plus sécurisées.

Par exemple, cet extrait de code génère un avertissement, car `strcpy` est dépréciée :

```cpp
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

L’avertissement de dépréciation est là pour vous indiquer que votre code peut présenter un risque. Si vous avez vérifié que votre code ne peut pas écraser la mémoire, vous avez plusieurs options. Vous pouvez choisir d’ignorer l’avertissement ; vous pouvez définir le symbole `_CRT_SECURE_NO_WARNINGS` avant les instructions include pour les en-têtes CRT pour supprimer l’avertissement, ou vous pouvez mettre à jour votre code pour utiliser `strcpy_s` :

```cpp
char szBuf[10];
strcpy_s(szBuf, 10, "test"); // security-enhanced _s function
```

Les surcharges de modèle fournissent des options supplémentaires. Si vous affectez à `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` la valeur 1, cela active des surcharges de modèle de fonctions CRT standard qui appellent automatiquement les variantes plus sécurisées. Si `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` a la valeur 1, aucune modification de votre code n’est nécessaire. Dans les coulisses, l’appel à `strcpy` est remplacé par un appel à `strcpy_s` avec l’argument de taille fourni automatiquement.

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char szBuf[10];
strcpy(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

La macro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` n’affecte pas les fonctions qui acceptent un nombre, par exemple `strncpy`. Pour activer les surcharges de modèle pour les fonctions de nombre, affectez à `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` la valeur 1. Avant cela, toutefois, vérifiez que votre code obtient le nombre de caractères, et non la taille de la mémoire tampon (une erreur courante). En outre, du code qui écrit explicitement une marque de fin null à la fin de la mémoire tampon après l’appel de fonction n’est pas nécessaire si la variante sécurisée est appelée. Si vous avez besoin du comportement de la troncation, consultez [_TRUNCATE](../c-runtime-library/truncate.md).

> [!NOTE]
>  La macro `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` nécessite que la valeur 1 soit également définie pour `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES`. Si `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` a la valeur 1 et `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` a la valeur 0, l’application n’effectue aucune surcharge de modèle.

Quand vous affectez à `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` la valeur 1, elle permet des surcharges de modèle des variantes sécurisées (noms se terminant par « _s »). Dans ce cas, si `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` a la valeur 1, une petite modification doit être apportée au code d’origine :

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char szBuf[10];
strcpy_s(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

Seul le nom de la fonction doit être modifié (en ajoutant « _s ») ; la surcharge de modèle prend soin de fournir l’argument de taille.

Par défaut, `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` et `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` ont la valeur 0 (sont désactivées) et `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` a la valeur 1 (est activée).

Notez que ces surcharges de modèle fonctionnent uniquement pour les tableaux statiques. Les mémoires tampons allouées dynamiquement nécessitent des modifications du code source supplémentaires. Nouvel examen des exemples ci-dessus :

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy(szBuf, "test"); // still deprecated; you have to change it to
                       // strcpy_s(szBuf, 10, "test");
```

Et de ceci :

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy_s(szBuf, "test"); // doesn't compile; you have to change it to
                         // strcpy_s(szBuf, 10, "test");
```

## <a name="see-also"></a>Voir aussi

[Fonctionnalités de sécurité dans la bibliothèque CRT](../c-runtime-library/security-features-in-the-crt.md)<br/>
[Fonctionnalités de bibliothèque CRT](../c-runtime-library/crt-library-features.md)
