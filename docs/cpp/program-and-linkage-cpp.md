---
title: Unités de traduction et liaison (C++)
ms.date: 12/11/2019
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
ms.openlocfilehash: e964a3c70c138caf8848e6a6366097cbfb90f548
ms.sourcegitcommit: f7ebdfc3a260778c2ef938747cba1376c70ced15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84108392"
---
# <a name="translation-units-and-linkage"></a>Unités de traduction et liaison

Dans un programme C++, un *symbole*, par exemple, un nom de variable ou de fonction, peut être déclaré autant de fois que possible dans son étendue, mais il ne peut être défini qu’une seule fois. Cette règle est la « règle de définition unique » (ODR). Une *déclaration* introduit (ou réintroduit) un nom dans le programme. Une *définition* introduit un nom. Si le nom représente une variable, une définition l’initialise explicitement. Une *définition de fonction* se compose de la signature et du corps de la fonction. Une définition de classe se compose du nom de la classe suivi d’un bloc qui répertorie tous les membres de la classe. (Les corps des fonctions membres peuvent éventuellement être définis séparément dans un autre fichier.)

L’exemple suivant illustre certaines déclarations :

```cpp
int i;
int f(int x);
class C;
```

L’exemple suivant montre quelques définitions :

```cpp
int i{42};
int f(int x){ return x * i; }
class C {
public:
   void DoSomething();
};
```

Un programme se compose d’une ou de plusieurs *unités de traduction*. Une unité de traduction se compose d’un fichier d’implémentation et de tous les en-têtes qu’il inclut directement ou indirectement. Les fichiers d’implémentation ont généralement l’extension de fichier *CPP* ou *cxx*. Les fichiers d’en-tête ont généralement l’extension *h* ou *HPP*. Chaque unité de traduction est compilée indépendamment par le compilateur. Une fois la compilation terminée, l’éditeur de liens fusionne les unités de traduction compilées en un seul *programme*. Les violations de la règle ODR apparaissent généralement en tant qu’erreurs de l’éditeur de liens. Les erreurs de l’éditeur de liens se produisent lorsque le même nom a deux définitions différentes dans des unités de traduction différentes.

En général, la meilleure façon de rendre une variable visible dans plusieurs fichiers consiste à la placer dans un fichier d’en-tête. Ajoutez ensuite une directive #include dans chaque fichier *CPP* qui requiert la déclaration. En ajoutant des *protections include* autour du contenu d’en-tête, vous vous assurez que les noms déclarés ne sont définis qu’une seule fois.

En C++ 20, les [modules](modules-cpp.md) sont introduits comme une alternative améliorée aux fichiers d’en-tête.

Dans certains cas, il peut être nécessaire de déclarer une variable globale ou une classe dans un fichier *CPP* . Dans ce cas, vous avez besoin d’un moyen d’indiquer au compilateur et à l’éditeur de liens le type de *liaison* du nom. Le type de liaison spécifie si le nom de l’objet s’applique uniquement à un fichier ou à tous les fichiers. Le concept de liaison s’applique uniquement aux noms globaux. Le concept de liaison ne s’applique pas aux noms déclarés dans une étendue. Une étendue est spécifiée par un ensemble d’accolades englobant telles que dans les définitions de la fonction ou de la classe.

## <a name="external-vs-internal-linkage"></a>Liaison externe et liaison interne

Une *fonction Free* est une fonction définie au niveau de la portée globale ou de l’espace de noms. Par défaut, les variables globales et les fonctions libres non const ont une *liaison externe*; ils sont visibles à partir de n’importe quelle unité de traduction du programme. Par conséquent, aucun autre objet global ne peut avoir ce nom. Un symbole avec *liaison interne* ou *aucune liaison* n’est visible que dans l’unité de traduction dans laquelle il est déclaré. Lorsqu’un nom a une liaison interne, le même nom peut exister dans une autre unité de traduction. Les variables déclarées dans des définitions de classe ou des corps de fonction n’ont aucune liaison.

Vous pouvez forcer un nom global à avoir une liaison interne en le déclarant explicitement comme **static**. Cela limite sa visibilité à la même unité de traduction dans laquelle elle est déclarée. Dans ce contexte, **static** signifie autre chose que lorsqu’il est appliqué à des variables locales.

Les objets suivants ont une liaison interne par défaut :

- objets const
- objets constexpr
- typedefs
- objets statiques dans la portée espace de noms

Pour donner une liaison externe d’objet const, déclarez-la comme **extern** et affectez-lui une valeur :

```cpp
extern const int value = 42;
```

Pour plus d’informations, consultez [extern](extern-cpp.md) .

## <a name="see-also"></a>Voir aussi

[Concepts de base](../cpp/basic-concepts-cpp.md)
