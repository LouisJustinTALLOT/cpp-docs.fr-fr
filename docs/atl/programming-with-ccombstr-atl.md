---
description: 'En savoir plus sur : programmation avec CComBSTR (ATL)'
title: Programmation avec CComBSTR (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
ms.openlocfilehash: 6c348d703aeaeba40f1f47b8f6fd0ee858b7babd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159217"
---
# <a name="programming-with-ccombstr-atl"></a>Programmation avec CComBSTR (ATL)

La classe de [CCOMBSTR](../atl/reference/ccombstr-class.md) ATL fournit un wrapper autour du type de données BSTR. Tandis que `CComBSTR` est un outil utile, il existe plusieurs situations qui nécessitent une attention.

- [Problèmes de conversion](#programmingwithccombstr_conversionissues)

- [Problèmes d’étendue](#programmingwithccombstr_scopeissues)

- [Libération explicite de l’objet CComBSTR](#programmingwithccombstr_explicitlyfreeing)

- [Utilisation d’objets CComBSTR dans des boucles](#programmingwithccombstr_usingloops)

- [Problèmes de fuite de mémoire](#programmingwithccombstr_memoryleaks)

## <a name="conversion-issues"></a><a name="programmingwithccombstr_conversionissues"></a> Problèmes de conversion

Bien que plusieurs `CComBSTR` méthodes convertissent automatiquement un argument de chaîne ANSI en Unicode, elles retournent toujours des chaînes de format Unicode. Pour reconvertir la chaîne de sortie en ANSI, utilisez une classe de conversion ATL. Pour plus d’informations sur les classes de conversion ATL, consultez [macros de conversion de chaînes ATL et MFC](reference/string-conversion-macros.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]

Si vous utilisez un littéral de chaîne pour modifier un `CComBSTR` objet, utilisez des chaînes à caractères larges. Cela réduira les conversions inutiles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]

## <a name="scope-issues"></a><a name="programmingwithccombstr_scopeissues"></a> Problèmes d’étendue

Comme avec n’importe quelle classe à comportement correct, `CComBSTR` libère ses ressources lorsqu’il est hors de portée. Si une fonction retourne un pointeur vers la `CComBSTR` chaîne, cela peut entraîner des problèmes, car le pointeur fait référence à la mémoire qui a déjà été libérée. Dans ce cas, utilisez la `Copy` méthode, comme indiqué ci-dessous.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]

## <a name="explicitly-freeing-the-ccombstr-object"></a><a name="programmingwithccombstr_explicitlyfreeing"></a> Libération explicite de l’objet CComBSTR

Il est possible de libérer explicitement la chaîne contenue dans l' `CComBSTR` objet avant que l’objet ne passe à l’étendue. Si la chaîne est libérée, l' `CComBSTR` objet n’est pas valide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]

## <a name="using-ccombstr-objects-in-loops"></a><a name="programmingwithccombstr_usingloops"></a> Utilisation d’objets CComBSTR dans des boucles

À mesure que la `CComBSTR` classe alloue une mémoire tampon pour effectuer certaines opérations, telles que l' `+=` opérateur ou la `Append` méthode, il n’est pas recommandé d’effectuer une manipulation de chaînes à l’intérieur d’une boucle serrée. Dans ces situations, `CStringT` offre de meilleures performances.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]

## <a name="memory-leak-issues"></a><a name="programmingwithccombstr_memoryleaks"></a> Problèmes de fuite de mémoire

La transmission de l’adresse d’un initialisé `CComBSTR` à une fonction en tant que paramètre **[out]** provoque une fuite de mémoire.

Dans l’exemple ci-dessous, la chaîne allouée pour contenir la chaîne `"Initialized"` est divulguée lorsque la fonction `MyGoodFunction` remplace la chaîne.

[!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]

Pour éviter la fuite, appelez la `Empty` méthode sur les `CComBSTR` objets existants avant de passer l’adresse en tant que paramètre **[out]** .

Notez que le même code ne provoquerait pas de fuite si le paramètre de la fonction était **[in, out]**.

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)<br/>
[CStringT (classe)](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[wstring](../standard-library/basic-string-class.md)<br/>
[Macros de conversion de chaînes](../atl/reference/string-conversion-macros.md)
