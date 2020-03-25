---
title: Fonctions utilisées par défaut et supprimées explicitement
ms.date: 11/04/2016
ms.assetid: 5a588478-fda2-4b3f-a279-db3967f5e07e
ms.openlocfilehash: b43588aac1d246c83f5281456625eeb0ff36b94d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179976"
---
# <a name="explicitly-defaulted-and-deleted-functions"></a>Fonctions utilisées par défaut et supprimées explicitement

En C++11, les fonctions utilisées par défaut et supprimées vous permettent de contrôler de façon explicite si les fonctions membres spéciales sont générées automatiquement. Les fonctions supprimées vous fournissent également un langage simple pour empêcher les promotions de type problématiques dans les arguments de fonctions de tous les types (les fonctions membres spéciales, ainsi que les fonctions membres normales et les fonctions non membres) qui provoqueraient autrement un appel de fonction indésirable.

## <a name="benefits-of-explicitly-defaulted-and-deleted-functions"></a>Avantages des fonctions utilisées par défaut et supprimées explicitement

En C++, le compilateur génère automatiquement le constructeur par défaut, le constructeur de copie, l'opérateur d'assignation de copie et le destructeur pour un type s'il ne déclare pas le sien. Ces fonctions sont connues sous le nom de *fonctions membres spéciales*, et c’est ce qui rend les types simples C++ définis par l’utilisateur dans se comporter comme les structures en C. Autrement dit, vous pouvez les créer, les copier et les détruire sans effort de codage supplémentaire. C++11 fournit la sémantique de déplacement au langage et ajoute le constructeur de déplacement et l'opérateur d'assignation de mouvement à la liste des fonctions membres spéciales que le compilateur peut générer automatiquement.

Cela est pratique pour les types simples, mais les types complexes définissent eux-mêmes souvent une ou plusieurs des fonctions membres spéciales, et cela peut empêcher d'autres fonctions membres spéciales d'être générées automatiquement. Dans la pratique :

- Si un constructeur est déclaré explicitement, aucun constructeur par défaut n'est automatiquement généré.

- Si un destructeur virtuel est déclaré explicitement, aucun destructeur par défaut n'est automatiquement généré.

- Si un constructeur de déplacement ou un opérateur d'assignation de déplacement est déclaré explicitement :

   - Aucun constructeur de copie n'est généré automatiquement.

   - Aucun opérateur d'assignation de copie n'est généré automatiquement.

- Si un constructeur de copie, un opérateur d'assignation de copie, un constructeur de déplacement, un opérateur d'assignation de mouvement ou un destructeur est déclaré explicitement :

   - Aucun constructeur de déplacement n'est généré automatiquement.

   - Aucun opérateur d'assignation de déplacement n'est généré automatiquement.

> [!NOTE]
> En outre, la norme C++11 spécifie les règles supplémentaires suivantes :
>
> - Si un constructeur de copie ou un destructeur est déclaré explicitement, la génération automatique de l'opérateur d'assignation de copie est déconseillée.
> - Si un opérateur d'assignation de copie ou un destructeur est déclaré explicitement, la génération automatique du constructeur de copie est déconseillée.
>
> Dans les deux cas, Visual Studio continue à générer automatiquement les fonctions nécessaires implicitement, sans émettre d'avertissement.

Les conséquences de ces règles peuvent également se répercuter dans la hiérarchie des objets. Par exemple, si, pour une raison quelconque, une classe de base ne peut pas avoir un constructeur par défaut qui peut être appelé à partir d’une classe dérivée (autrement dit, un constructeur **public** ou **protégé** qui ne prend aucun paramètre), une classe qui en dérive ne peut pas générer automatiquement son propre constructeur par défaut.

Ces règles peuvent compliquer l'implémentation d'idiomes C++ qui devraient pourtant être simples, courants et de types définis par l'utilisateur (par exemple, rendre un type défini par l'utilisateur impossible à copier en déclarant le constructeur de copie et l'opérateur d'assignation de copie en privé et en ne les définissant pas).

```cpp
struct noncopyable
{
  noncopyable() {};

private:
  noncopyable(const noncopyable&);
  noncopyable& operator=(const noncopyable&);
};
```

Avant C++11, cet extrait de code était la forme idiomatique des types qu'il était impossible de copier. Toutefois, il présente plusieurs problèmes :

- Le constructeur de copie doit être déclaré de manière privée pour le masquer, mais comme il n'est pas déclaré du tout, la génération automatique du constructeur par défaut est bloquée. Vous devez définir explicitement le constructeur par défaut si vous en souhaitez un, même s'il ne fait rien.

- Même si le constructeur par défaut défini explicitement ne fait rien, il est considéré comme étant non trivial par le compilateur. Il est moins efficace qu'un constructeur par défaut généré automatiquement et empêche un type `noncopyable` d'être un type POD réel.

- Bien que le constructeur de copie et l'opérateur d'assignation de copie soient masqués vis-à-vis du code externe, les fonctions membres et les amis de `noncopyable` peuvent tout de même les voir et les appeler. S'ils sont déclarés mais non définis, leur appel entraîne une erreur de l'éditeur de liens.

- Bien qu'il s'agisse d'un idiome couramment accepté, l'intention n'est pas claire tant que vous ne comprenez pas toutes les règles de génération automatique des fonctions membres spéciales.

En C++11, l'idiome non copiable peut être implémenté de façon plus simple.

```cpp
struct noncopyable
{
  noncopyable() =default;
  noncopyable(const noncopyable&) =delete;
  noncopyable& operator=(const noncopyable&) =delete;
};
```

Notez comment les problèmes d'idiome pré-C++11 sont résolus :

- La génération du constructeur par défaut est toujours empêchée en déclarant le constructeur de copie, mais vous pouvez la réactiver en la définissant comme valeur par défaut explicite.

- Les fonctions membres spéciales utilisées par défaut explicitement sont toujours considérées comme triviales ; par conséquent, il n'y a aucune altération des performances et un type `noncopyable` peut être un type POD réel.

- Le constructeur de copie et l'opérateur d'assignation de copie sont publics, mais supprimés. La définition ou l'appel d'une fonction supprimée constitue une erreur de compilation.

- L'intention est claire pour toute personne qui comprend `=default` et `=delete`. Vous ne devez pas comprendre les règles pour la génération automatique des fonctions membres spéciales.

Des idiomes similaires existent pour créer des types définis par l'utilisateur qui ne peuvent pas être déplacés, qui ne peuvent qu'être alloués dynamiquement ou qui ne peuvent pas être alloués dynamiquement. Chacun de ces idiomes possède des implémentations pré-C++11 qui connaissent des problèmes similaires, et qui sont résolus de façon identique en C++11 en les implémentant en termes de fonctions membres spéciales utilisées par défaut et supprimées.

## <a name="explicitly-defaulted-functions"></a>Fonctions utilisées par défaut explicitement

Vous pouvez définir par défaut n'importe laquelle des fonctions membres spéciales : pour établir explicitement que la fonction membre spéciale utilise l'implémentation par défaut, pour définir la fonction membre spéciale avec un qualificateur d'accès non public ou pour rétablir une fonction membre spéciale dont la génération automatique a été empêchée par d'autres circonstances.

Vous définissez par défaut une fonction membre spéciale en la déclarant comme dans cet exemple :

```cpp
struct widget
{
  widget()=default;

  inline widget& operator=(const widget&);
};

inline widget& widget::operator=(const widget&) =default;
```

Notez que vous pouvez utiliser par défaut une fonction membre spéciale en dehors du corps d'une classe tant qu'elle peut être inline.

Étant donné les avantages des fonctions membres spéciales ordinaires en termes de performance, nous vous recommandons de préférer les fonctions membres spéciales générées automatiquement aux corps de fonction vides lorsque vous souhaitez rétablir le comportement par défaut. Vous pouvez effectuer cette opération en définissant explicitement par défaut la fonction membre spéciale, ou en ne la déclarant pas (et en ne déclarant pas non plus d'autres fonctions membres spéciales qui l'empêcheraient d'être générée automatiquement.)

## <a name="deleted-functions"></a>Fonctions supprimées

Vous pouvez supprimer des fonctions membres spéciales ainsi que des fonctions membres normales et des fonctions non-membres pour empêcher qu'elles ne soient définies ou appelées. La suppression des fonctions membres spéciales offre un moyen plus net d'empêcher le compilateur de générer des fonctions membres spéciales que vous ne souhaitez pas. La fonction doit être supprimée lorsqu'elle est déclarée ; elle ne peut pas être supprimée après de la façon dont une fonction peut-être déclarée et utilisée ensuite par défaut.

```cpp
struct widget
{
  // deleted operator new prevents widget from being dynamically allocated.
  void* operator new(std::size_t) = delete;
};
```

La suppression des fonctions membres ou non-membres normales empêche les promotions de type problématiques de provoquer l'appel d'une fonction non voulue. Cela fonctionne, car les fonctions supprimées participent toujours à la résolution de surcharge et fournissent une meilleure correspondance que la fonction qui peut être appelée une fois que les types sont promus. L'appel de fonction résout la fonction la plus spécifique mais supprimée et provoque une erreur du compilateur.

```cpp
// deleted overload prevents call through type promotion of float to double from succeeding.
void call_with_true_double_only(float) =delete;
void call_with_true_double_only(double param) { return; }
```

Notez que dans l’exemple précédent, l’appel de `call_with_true_double_only` à l’aide d’un argument **float** provoque une erreur du compilateur, mais l’appel de `call_with_true_double_only` à l’aide d’un argument **int** ne le ferait pas ; dans le cas **int** , l’argument sera promu de **int** en **double** et appellera correctement la version **double** de la fonction, même si ce n’est peut-être pas ce qui est prévu. Pour garantir qu’un appel à cette fonction à l’aide d’un argument non double provoque une erreur du compilateur, vous pouvez déclarer une version de modèle de la fonction supprimée.

```cpp
template < typename T >
void call_with_true_double_only(T) =delete; //prevent call through type promotion of any T to double from succeeding.

void call_with_true_double_only(double param) { return; } // also define for const double, double&, etc. as needed.
```
