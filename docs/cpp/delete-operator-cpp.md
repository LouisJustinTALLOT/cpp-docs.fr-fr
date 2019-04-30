---
title: delete, opérateur (C++)
ms.date: 11/04/2016
f1_keywords:
- delete_cpp
helpviewer_keywords:
- delete keyword [C++], syntax
- delete keyword [C++], deallocating objects
- delete keyword [C++]
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
ms.openlocfilehash: 5e4f5685ea1bb8cd7c405373ba774fe36af08672
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398964"
---
# <a name="delete-operator-c"></a>delete, opérateur (C++)

Libère un bloc de mémoire.

## <a name="syntax"></a>Syntaxe

```
[::] delete cast-expression
[::] delete [ ] cast-expression
```

## <a name="remarks"></a>Notes

Le *cast-expression* argument doit être un pointeur vers un bloc de mémoire précédemment alloué pour un objet créé avec le [nouvel opérateur](../cpp/new-operator-cpp.md). Le **supprimer** opérateur a un résultat de type **void** et par conséquent, ne retourne pas de valeur. Exemple :

```cpp
CDialog* MyDialog = new CDialog;
// use MyDialog
delete MyDialog;
```

À l’aide de **supprimer** sur un pointeur vers un objet non alloué avec **nouveau** donne des résultats imprévisibles. Vous pouvez, toutefois, utiliser **supprimer** sur un pointeur avec la valeur 0. Cette configuration signifie que, lorsque **nouveau** retourne 0 en cas d’échec, la suppression du résultat d’un échec **nouveau** opération ne présente aucun danger. Consultez [le nouveau et supprimer des opérateurs](../cpp/new-and-delete-operators.md) pour plus d’informations.

Le **nouveau** et **supprimer** opérateurs peuvent également être utilisés pour les types intégrés, y compris les tableaux. Si `pointer` fait référence à un tableau, placez des crochets vides avant `pointer` :

```cpp
int* set = new int[100];
//use set[]
delete [] set;
```

À l’aide de la **supprimer** opérateur sur un objet libère sa mémoire. Un programme qui déréférence un pointeur après la suppression de l'objet peut avoir des résultats imprévisibles ou se bloquer.

Lorsque **supprimer** est utilisé pour libérer la mémoire pour un objet de classe C++, destructeur de l’objet est appelé avant la libération de la mémoire de l’objet (si l’objet a un destructeur).

Si l’opérande de le **supprimer** opérateur est une l-value modifiable, sa valeur n’est pas définie une fois que l’objet est supprimé.

## <a name="using-delete"></a>Utilisation de delete

Il existe deux variantes syntaxiques pour le [opérateur delete](../cpp/delete-operator-cpp.md): un pour les objets uniques et l’autre pour les tableaux d’objets. Le fragment de code suivant illustre les différences entre ces variantes :

```cpp
// expre_Using_delete.cpp
struct UDType
{
};

int main()
{
   // Allocate a user-defined object, UDObject, and an object
   //  of type double on the free store using the
   //  new operator.
   UDType *UDObject = new UDType;
   double *dObject = new double;
   // Delete the two objects.
   delete UDObject;
   delete dObject;
   // Allocate an array of user-defined objects on the
   // free store using the new operator.
   UDType (*UDArr)[7] = new UDType[5][7];
   // Use the array syntax to delete the array of objects.
   delete [] UDArr;
}
```

Les deux cas suivants génèrent des résultats indéfinis : en utilisant la forme de tableau delete (delete [ ]) sur un objet et en utilisant la forme nonarray de delete sur un tableau.

## <a name="example"></a>Exemple

Pour obtenir des exemples d’utilisation de **supprimer**, consultez [nouvel opérateur](../cpp/new-operator-cpp.md).

## <a name="how-delete-works"></a>Fonctionnement de delete

L’opérateur delete appelle la fonction **opérateur delete**.

Pour les objets pas du type de classe ([classe](../cpp/class-cpp.md), [struct](../cpp/struct-cpp.md), ou [union](../cpp/unions.md)), l’opérateur delete global est appelé. Pour les objets de type classe, le nom de la fonction de désallocation est résolu dans la portée globale si l'expression de suppression commence par l'opérateur de résolution de portée unaire (::). Sinon, l'opérateur delete appelle le destructeur pour un objet avant de désallouer la mémoire (si le pointeur n'est pas null). L'opérateur delete peut être défini pour chaque classe ; si cette définition n'existe pas pour une classe donnée, l'opérateur de suppression global est appelé. Si l'expression de suppression est utilisée pour désallouer un objet de classe dont le type statique a un destructeur virtuel, la fonction de désallocation est résolue par l'intermédiaire du destructeur virtuel du type dynamique de l'objet.

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[new et delete, opérateurs](../cpp/new-and-delete-operators.md)