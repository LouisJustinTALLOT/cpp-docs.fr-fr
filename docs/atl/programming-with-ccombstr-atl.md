---
title: Programmation avec CComBSTR (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
ms.openlocfilehash: 020c2d18c721e658d15bb1451039154ae50b99f6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321796"
---
# <a name="programming-with-ccombstr-atl"></a>Programmation avec CComBSTR (ATL)

La classe ATL [CComBSTR](../atl/reference/ccombstr-class.md) fournit un emballage autour du type de données BSTR. Bien `CComBSTR` qu’il s’agit d’un outil utile, il y a plusieurs situations qui nécessitent la prudence.

- [Problèmes de conversion](#programmingwithccombstr_conversionissues)

- [Problèmes de portée](#programmingwithccombstr_scopeissues)

- [Libérer explicitement l’objet CComBSTR](#programmingwithccombstr_explicitlyfreeing)

- [Utilisation d’objets CComBSTR en boucles](#programmingwithccombstr_usingloops)

- [Problèmes de fuite de mémoire](#programmingwithccombstr_memoryleaks)

## <a name="conversion-issues"></a><a name="programmingwithccombstr_conversionissues"></a>Problèmes de conversion

Bien `CComBSTR` que plusieurs méthodes convertiront automatiquement un argument de chaîne ANSI en Unicode, les méthodes retourneront toujours les chaînes de format Unicode. Pour convertir la chaîne de sortie en ANSI, utilisez une classe de conversion ATL. Pour plus d’informations sur les classes de conversion ATL, voir [ATL et MFC String Conversion Macros](reference/string-conversion-macros.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]

Si vous utilisez une chaîne littérale `CComBSTR` pour modifier un objet, utilisez de larges chaînes de caractère. Cela réduira les conversions inutiles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]

## <a name="scope-issues"></a><a name="programmingwithccombstr_scopeissues"></a>Problèmes de portée

Comme avec n’importe quelle `CComBSTR` classe bien élevée, libérera ses ressources quand elle sortira de portée. Si une fonction renvoie `CComBSTR` un pointeur à la chaîne, cela peut causer des problèmes, car le pointeur fera référence à la mémoire qui a déjà été libérée. Dans ces cas, `Copy` utilisez la méthode, comme indiqué ci-dessous.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]

## <a name="explicitly-freeing-the-ccombstr-object"></a><a name="programmingwithccombstr_explicitlyfreeing"></a>Libérer explicitement l’objet CComBSTR

Il est possible de libérer explicitement `CComBSTR` la chaîne contenue dans l’objet avant que l’objet ne dépasse la portée. Si la ficelle est `CComBSTR` libérée, l’objet est invalide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]

## <a name="using-ccombstr-objects-in-loops"></a><a name="programmingwithccombstr_usingloops"></a>Utilisation d’objets CComBSTR en boucles

Comme `CComBSTR` la classe alloue un tampon pour `+=` effectuer `Append` certaines opérations, telles que l’opérateur ou la méthode, il n’est pas recommandé que vous effectuez la manipulation des cordes à l’intérieur d’une boucle serrée. Dans ces `CStringT` situations, offre de meilleures performances.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]

## <a name="memory-leak-issues"></a><a name="programmingwithccombstr_memoryleaks"></a>Problèmes de fuite de mémoire

Passer l’adresse d’un paramètre initialisé `CComBSTR` à une fonction comme paramètre **[out]** provoque une fuite de mémoire.

Dans l’exemple ci-dessous, la `"Initialized"` chaîne allouée `MyGoodFunction` à la prise de la chaîne est divulguée lorsque la fonction remplace la chaîne.

[!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]

Pour éviter la fuite, appelez la `Empty` méthode sur les objets existants `CComBSTR` avant de passer l’adresse comme un paramètre **[out].**

Notez que le même code ne causerait pas de fuite si le paramètre de la fonction était **[dans, dehors]**.

## <a name="see-also"></a>Voir aussi

[Concepts liés à la](../atl/active-template-library-atl-concepts.md)<br/>
[Classe CStringT](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[wstring](../standard-library/basic-string-class.md)<br/>
[Macro de conversion de cordes](../atl/reference/string-conversion-macros.md)
