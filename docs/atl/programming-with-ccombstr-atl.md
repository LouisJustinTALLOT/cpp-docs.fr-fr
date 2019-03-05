---
title: Programmation avec CComBSTR (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
ms.openlocfilehash: 806d23730a0657fc1e0c154e20dc9abd62f7e8af
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259410"
---
# <a name="programming-with-ccombstr-atl"></a>Programmation avec CComBSTR (ATL)

La classe ATL [CComBSTR](../atl/reference/ccombstr-class.md) fournit un wrapper autour du type de données BSTR. Bien que `CComBSTR` est un outil utile, il existe plusieurs situations nécessitant une attention.

- [Problèmes de conversion](#programmingwithccombstr_conversionissues)

- [Problèmes de portée](#programmingwithccombstr_scopeissues)

- [Libération explicite de l’objet CComBSTR](#programmingwithccombstr_explicitlyfreeing)

- [Utilisation d’objets CComBSTR dans des boucles](#programmingwithccombstr_usingloops)

- [Problèmes de fuite de mémoire](#programmingwithccombstr_memoryleaks)

##  <a name="programmingwithccombstr_conversionissues"></a> Problèmes de conversion

Bien que plusieurs `CComBSTR` méthodes convertissent automatiquement un argument de chaîne ANSI en Unicode, les méthodes retournent toujours les chaînes au format Unicode. Pour convertir la chaîne de sortie en ANSI, utilisez une classe de conversion ATL. Pour plus d’informations sur les classes de conversion ATL, consultez [Macros de Conversion de chaîne de MFC et ATL](reference/string-conversion-macros.md).

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]

Si vous utilisez un littéral de chaîne pour modifier un `CComBSTR` de l’objet, utilisez des chaînes de caractères larges. Cela permet de réduire les conversions inutiles.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]

##  <a name="programmingwithccombstr_scopeissues"></a> Problèmes de portée

Comme avec n’importe quelle classe se comportant bien, `CComBSTR` permettra de libérer ses ressources lorsqu’il devient hors de portée. Si une fonction retourne un pointeur vers le `CComBSTR` chaîne, cela peut entraîner des problèmes, comme le pointeur de référence de la mémoire qui a déjà été libéré. Dans ces cas, utilisez le `Copy` (méthode), comme indiqué ci-dessous.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]

##  <a name="programmingwithccombstr_explicitlyfreeing"></a> Libération explicite de l’objet CComBSTR

Il est possible de libérer explicitement la chaîne contenue dans le `CComBSTR` avant que l’objet sort de l’étendue de l’objet. Si la chaîne est libérée, le `CComBSTR` objet n’est pas valide.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]

##  <a name="programmingwithccombstr_usingloops"></a> Utilisation d’objets CComBSTR dans des boucles

Comme le `CComBSTR` classe alloue une mémoire tampon pour effectuer certaines opérations, telles que la `+=` opérateur ou `Append` (méthode), il est déconseillé d’effectuer de manipulation de chaînes à l’intérieur d’une boucle serrée. Dans ces situations, `CStringT` offre de meilleures performances.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]

##  <a name="programmingwithccombstr_memoryleaks"></a> Problèmes de fuite de mémoire

En passant l’adresse d’initialisé `CComBSTR` à une fonction comme un **[out]** paramètre entraîne une fuite de mémoire.

Dans l’exemple ci-dessous, la chaîne allouée pour contenir la chaîne `"Initialized"` fuite lorsque la fonction `MyGoodFunction` remplace la chaîne.

[!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]

Pour éviter la fuite, appelez le `Empty` méthode existant `CComBSTR` objets avant de transmettre l’adresse en tant qu’un **[out]** paramètre.

Notez que le même code ne serait pas provoquer une fuite si le paramètre de la fonction a été **[dans, out]**.

## <a name="see-also"></a>Voir aussi

[Concepts](../atl/active-template-library-atl-concepts.md)<br/>
[CStringT, classe](../atl-mfc-shared/reference/cstringt-class.md)<br/>
[wstring](../standard-library/basic-string-class.md)<br/>
[Macros de conversion de chaînes](../atl/reference/string-conversion-macros.md)
