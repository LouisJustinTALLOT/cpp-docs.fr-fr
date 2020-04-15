---
title: Unités de traduction et liaison (CMD)
ms.date: 12/11/2019
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
ms.openlocfilehash: 791ec53d4df863b218db463f2b9b9401bf6f466d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374314"
---
# <a name="translation-units-and-linkage"></a>Unités de traduction et liaison

Dans un programme C, un *symbole,* par exemple une variable ou un nom de fonction, peut être déclaré n’importe quel nombre de fois dans son champ d’application, mais il ne peut être défini qu’une seule fois. Cette règle est la « règle d’une définition » (ODR). Une *déclaration* introduit (ou réintroduira) un nom dans le programme. Une *définition* introduit un nom. Si le nom représente une variable, une définition l’initialise explicitement. Une définition de *fonction* se compose de la signature plus le corps de fonction. Une définition de classe se compose du nom de classe suivi d’un bloc qui répertorie tous les membres de la classe. (Les organes des fonctions des membres peuvent être définis séparément dans un autre fichier.)

L’exemple suivant montre quelques déclarations :

```cpp
int i;
int f(int x);
class C;
```

L’exemple suivant montre quelques définitions :

```cpp
int i{42};
int f(int x){ return x * i; }
class C {
public:
   void DoSomething();
};
```

Un programme se compose d’une ou plusieurs unités de *traduction*. Une unité de traduction se compose d’un fichier de mise en œuvre et de tous les en-têtes qu’elle inclut directement ou indirectement. Les fichiers de mise en œuvre ont généralement une extension de fichier de *cpp* ou *cxx*. Les fichiers d’en-tête ont généralement une extension de *h* ou *hpp*. Chaque unité de traduction est compilée indépendamment par le compilateur. Une fois la compilation terminée, le linker fusionne les unités de traduction compilées en un seul *programme.* Les violations de la règle ODR apparaissent généralement comme des erreurs de liaison. Les erreurs de liaison se produisent lorsque le même nom a deux définitions différentes dans différentes unités de traduction.

En général, la meilleure façon de rendre une variable visible sur plusieurs fichiers est de la mettre dans un fichier d’en-tête. Ensuite, ajoutez une directive #include dans chaque fichier *cpp* qui exige la déclaration. En ajoutant *inclure des gardes* autour du contenu de l’en-tête, vous vous assurez que les noms qu’il déclare ne sont définis qu’une seule fois.

Dans le C 20, les modules sont [introduits](modules-cpp.md) comme une alternative améliorée aux fichiers d’en-tête.

Dans certains cas, il peut être nécessaire de déclarer une variable ou une classe globale dans un fichier *cpp.* Dans ces cas, vous avez besoin d’un moyen de dire au compilateur et à l’unie quel type de *lien* le nom a. Le type de lien précise si le nom de l’objet s’applique uniquement au seul fichier, ou à tous les fichiers. Le concept de lien ne s’applique qu’aux noms mondiaux. Le concept de lien ne s’applique pas aux noms déclarés dans une portée. Une portée est spécifiée par un ensemble d’accolades d’enceintes telles que dans les définitions de fonction ou de classe.

## <a name="external-vs-internal-linkage"></a>Liaison externe par rapport à la liaison interne

Une *fonction libre* est une fonction qui est définie à la portée globale ou namespace. Les variables globales non const et les fonctions libres par défaut ont *un lien externe*; ils sont visibles à partir de n’importe quelle unité de traduction dans le programme. Par conséquent, aucun autre objet global ne peut avoir ce nom. Un symbole avec *lien interne* ou aucun *lien n’est* visible uniquement au sein de l’unité de traduction dans laquelle il est déclaré. Lorsqu’un nom a un lien interne, le même nom peut exister dans une autre unité de traduction. Les variables déclarées avec les définitions de classe ou les organismes de fonction n’ont aucun lien.

Vous pouvez forcer un nom global à avoir un lien interne en le déclarant explicitement comme **statique**. Cela limite sa visibilité à la même unité de traduction dans laquelle elle est déclarée. Dans ce contexte, **la statique** signifie quelque chose de différent de celui qui est appliqué aux variables locales.

Les objets suivants ont un lien interne par défaut :

- objets de cône
- objets constexpr
- typedefs
- objets statiques dans la portée de l’espace de nom

Pour donner à un objet de cône un lien externe, déclarez-le comme **arrière** et attribuez-lui une valeur :

```cpp
extern const int value = 42;
```

Voir [l’extern pour](extern-cpp.md) plus d’informations.

## <a name="see-also"></a>Voir aussi

[Concepts de base](../cpp/basic-concepts-cpp.md)
