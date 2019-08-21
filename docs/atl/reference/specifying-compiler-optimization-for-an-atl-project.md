---
title: Spécification de l’optimisation du compilateur pour un projet ATL
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
ms.openlocfilehash: c3b00823cb33be952451c3cc9e370c99140acc3c
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630614"
---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>Spécification de l’optimisation du compilateur pour un projet ATL

Par défaut, l' [Assistant contrôle ATL](../../atl/reference/atl-control-wizard.md) génère de nouvelles classes avec la macro ATL_NO_VTABLE, comme suit:

```
class ATL_NO_VTABLE CProjName
{
...
};
```

ATL définit ensuite _ATL_NO_VTABLE comme suit:

```
#ifdef _ATL_DISABLE_NO_VTABLE
#define ATL_NO_VTABLE
#else
#define ATL_NO_VTABLE __declspec(novtable)
#endif
```

Si vous ne définissez pas _ATL_DISABLE_NO_VTABLE, la macro ATL_NO_VTABLE s’étend à `declspec(novtable)`. L' `declspec(novtable)`utilisation de dans une déclaration de classe empêche l’initialisation du pointeur vtable dans le constructeur et le destructeur de classe. Quand vous générez votre projet, l’éditeur de liens élimine le vtable et toutes les fonctions vers lesquelles vtable pointe.

Vous devez utiliser ATL_NO_VTABLE, et par `declspec(novtable)`conséquent, avec uniquement les classes de base qui ne peuvent pas être créées directement. Vous ne devez pas `declspec(novtable)` utiliser avec la classe la plus dérivée dans votre projet, car cette classe (généralement [CComObject](../../atl/reference/ccomobject-class.md), [CComAggObject](../../atl/reference/ccomaggobject-class.md)ou [CComPolyObject](../../atl/reference/ccompolyobject-class.md)) Initialise le pointeur vtable pour votre projet.

Vous ne devez pas appeler des fonctions virtuelles à partir du constructeur d' `declspec(novtable)`un objet qui utilise. Vous devez transférer ces appels à la méthode [FinalConstruct](ccomobjectrootex-class.md#finalconstruct) .

Si vous ne savez pas si vous devez utiliser le `declspec(novtable)` modificateur, vous pouvez supprimer la macro ATL_NO_VTABLE de toutes les définitions de classe, ou vous pouvez la désactiver globalement en spécifiant

```
#define _ATL_DISABLE_NO_VTABLE
```

dans *pch. h* (*stdafx. h* dans Visual Studio 2017 et versions antérieures), avant l’inclusion de tous les autres fichiers d’en-tête ATL.

## <a name="see-also"></a>Voir aussi

[Assistant Projet ATL](../../atl/reference/atl-project-wizard.md)<br/>
[Types de projets C++ dans Visual Studio](../../build/reference/visual-cpp-project-types.md)<br/>
[Programmation avec ATL et le code C Run-Time](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[Principes de base des objets ATL COM](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[novtable](../../cpp/novtable.md)<br/>
[Configurations de projet ATL par défaut](../../atl/reference/default-atl-project-configurations.md)
