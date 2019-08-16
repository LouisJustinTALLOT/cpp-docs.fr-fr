---
title: delete, opérateur (C++)
ms.date: 08/12/2019
f1_keywords:
- delete_cpp
helpviewer_keywords:
- delete keyword [C++], syntax
- delete keyword [C++], deallocating objects
- delete keyword [C++]
ms.assetid: de39c900-3f57-489c-9598-dcb73c4b3930
ms.openlocfilehash: 3b00bf78d286ba530dee85240236a2a9ea171113
ms.sourcegitcommit: a146b169664c001406a0cccc7fbda1b8d7be5078
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69024645"
---
# <a name="delete-operator-c"></a>delete, opérateur (C++)

Libère un bloc de mémoire.

## <a name="syntax"></a>Syntaxe

> [`::`] `delete` *expression cast*\
> [`::`] `delete []` *expression cast*

## <a name="remarks"></a>Notes

L’argument *Cast-expression* doit être un pointeur vers un bloc de mémoire précédemment alloué pour un objet créé avec l' [opérateur New](../cpp/new-operator-cpp.md). L’opérateur **Delete** a un résultat de type **void** et, par conséquent, ne retourne pas de valeur. Par exemple : 

```cpp
CDialog* MyDialog = new CDialog;
// use MyDialog
delete MyDialog;
```

L’utilisation de **Delete** sur un pointeur vers un objet non alloué avec **New** donne des résultats imprévisibles. Toutefois, vous pouvez utiliser **Delete** sur un pointeur avec la valeur 0. Cette configuration signifie que, lorsque **New** retourne 0 en cas d’échec, la suppression du résultat d’une **nouvelle** opération n’est pas sans incidence. Pour plus d’informations, consultez [les opérateurs New et Delete](../cpp/new-and-delete-operators.md).

Les opérateurs **New** et **Delete** peuvent également être utilisés pour les types intégrés, y compris les tableaux. Si `pointer` fait référence à un tableau, placez les crochets`[]`vides ( `pointer`) avant:

```cpp
int* set = new int[100];
//use set[]
delete [] set;
```

L’utilisation de l’opérateur **Delete** sur un objet libère sa mémoire. Un programme qui déréférence un pointeur après la suppression de l'objet peut avoir des résultats imprévisibles ou se bloquer.

Quand la **suppression** est utilisée pour libérer de la mémoire C++ pour un objet de classe, le destructeur de l’objet est appelé avant la libération de la mémoire de l’objet (si l’objet a un destructeur).

Si l’opérande de l’opérateur **Delete** est une l-value modifiable, sa valeur n’est pas définie une fois que l’objet a été supprimé.

Si l’option de compilateur [/SDL (activer des vérifications de sécurité supplémentaires)](/cpp/build/reference/sdl-enable-additional-security-checks) est spécifiée, l’opérande de l’opérateur **Delete** est défini sur une valeur non valide après la suppression de l’objet.

## <a name="using-delete"></a>Utilisation de delete

Il existe deux variantes syntaxiques pour l' [opérateur delete](../cpp/delete-operator-cpp.md): une pour les objets uniques et l’autre pour les tableaux d’objets. Le fragment de code suivant montre comment ils diffèrent:

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

Les deux cas suivants produisent des résultats non définis: à l’aide de la forme de`delete []`tableau de Delete () sur un objet et à l’aide de la forme non tableau de Delete sur un tableau.

## <a name="example"></a>Exemple

Pour obtenir des exemples d’utilisation de **Delete**, consultez [New, opérateur](../cpp/new-operator-cpp.md).

## <a name="how-delete-works"></a>Fonctionnement de delete

L’opérateur delete appelle la fonction **operator delete**.

Pour les objets qui ne sont pas de type classe ([classe](../cpp/class-cpp.md), [struct](../cpp/struct-cpp.md)ou [Union](../cpp/unions.md)), l’opérateur de suppression global est appelé. Pour les objets de type classe, le nom de la fonction de désallocation est résolu dans la portée globale si l’expression de suppression commence par l’opérateur`::`de résolution de portée unaire (). Sinon, l'opérateur delete appelle le destructeur pour un objet avant de désallouer la mémoire (si le pointeur n'est pas null). L'opérateur delete peut être défini pour chaque classe ; si cette définition n'existe pas pour une classe donnée, l'opérateur de suppression global est appelé. Si l'expression de suppression est utilisée pour désallouer un objet de classe dont le type statique a un destructeur virtuel, la fonction de désallocation est résolue par l'intermédiaire du destructeur virtuel du type dynamique de l'objet.

## <a name="see-also"></a>Voir aussi

[Expressions avec opérateurs unaires](../cpp/expressions-with-unary-operators.md)\
[Mots clés](../cpp/keywords-cpp.md)\
[new et delete, opérateurs](../cpp/new-and-delete-operators.md)