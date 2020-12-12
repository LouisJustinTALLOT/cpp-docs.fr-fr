---
description: 'En savoir plus sur : classe d’exception'
title: exception, classe
ms.date: 11/04/2016
f1_keywords:
- exception/std::exception
helpviewer_keywords:
- exception class
ms.assetid: 4f181f67-5888-4b50-89a6-745091ffb2fe
ms.openlocfilehash: a2061a2609017872145b12b4863e939788a123cf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324447"
---
# <a name="exception-class"></a>exception, classe

La classe sert de classe de base pour toutes les exceptions levées par certaines expressions et par la bibliothèque C++ Standard.

## <a name="syntax"></a>Syntaxe

```cpp
class exception {
   public:
   exception();
   exception(const char* const &message);
   exception(const char* const &message, int);
   exception(const exception &right);
   exception& operator=(const exception &right);
   virtual ~exception();
   virtual const char *what() const;
};
```

## <a name="remarks"></a>Notes

Plus précisément, cette classe de base est la racine des classes d’exception standard définies dans [\<stdexcept>](../standard-library/stdexcept.md) . La valeur de chaîne C retournée par `what` est non définie par le constructeur par défaut, mais peut être définie par les constructeurs pour certaines classes dérivées comme une chaîne C définie par l’implémentation. Aucune des fonctions membres ne lève d'exception.

Le **`int`** paramètre vous permet de spécifier qu’aucune mémoire ne doit être allouée. La valeur de **`int`** est ignorée.

> [!NOTE]
> Les constructeurs `exception(const char* const &message)` et `exception(const char* const &message, int)` sont des extensions Microsoft pour la bibliothèque C++ Standard.

## <a name="example"></a>Exemple

Pour obtenir des exemples d’utilisation des classes d’exceptions standard qui héritent de la `exception` classe, consultez l’une des classes définies dans [\<stdexcept>](../standard-library/stdexcept.md) .
