---
title: Programmation avec CComBSTR (ATL) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CComBSTR class, programming with
- Unicode, using CComBSTR [ATL]
ms.assetid: d3bd0851-d132-4be9-9c4c-6ccba17acb2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b957cca4ff1af93d3f62ab0bf667462c91b81bba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32357855"
---
# <a name="programming-with-ccombstr-atl"></a>Programmation avec CComBSTR (ATL)
La classe ATL [CComBSTR](../atl/reference/ccombstr-class.md) fournit un wrapper autour de le `BSTR` type de données. Alors que `CComBSTR` est un outil utile, il existe plusieurs situations nécessitant une attention.  
  
-   [Problèmes de conversion](#programmingwithccombstr_conversionissues)  
  
-   [Problèmes de portée](#programmingwithccombstr_scopeissues)  
  
-   [Libération explicite de l’objet CComBSTR](#programmingwithccombstr_explicitlyfreeing)  
  
-   [Utilisation d’objets CComBSTR dans des boucles](#programmingwithccombstr_usingloops)  
  
-   [Problèmes de fuite de mémoire](#programmingwithccombstr_memoryleaks)  
  
##  <a name="programmingwithccombstr_conversionissues"></a> Problèmes de conversion  
 Bien que plusieurs `CComBSTR` méthodes convertissent automatiquement un argument de chaîne ANSI en Unicode, les méthodes retournera toujours des chaînes au format Unicode. Pour convertir la chaîne de sortie en ANSI, utilisez une classe de conversion ATL. Pour plus d’informations sur les classes de conversion ATL, consultez [ATL et MFC Macros de Conversion de chaînes](reference/string-conversion-macros.md).  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#114](../atl/codesnippet/cpp/programming-with-ccombstr-atl_1.cpp)]  
  
 Si vous utilisez un littéral de chaîne pour modifier un `CComBSTR` de l’objet, utilisez des chaînes à caractères larges. Cela permet de réduire les conversions inutiles.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#115](../atl/codesnippet/cpp/programming-with-ccombstr-atl_2.cpp)]  
  
##  <a name="programmingwithccombstr_scopeissues"></a> Problèmes de portée  
 Comme avec toute classe valide, `CComBSTR` permettra de libérer ses ressources lorsqu’il devient hors de portée. Si une fonction retourne un pointeur vers le `CComBSTR` chaîne, cela peut provoquer des problèmes, le pointeur de la référence de la mémoire qui a déjà été libéré. Dans ces cas, utilisez le **copie** méthode, comme indiqué ci-dessous.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#116](../atl/codesnippet/cpp/programming-with-ccombstr-atl_3.cpp)]  
  
##  <a name="programmingwithccombstr_explicitlyfreeing"></a> Libération explicite de l’objet CComBSTR  
 Il est possible de libérer explicitement la chaîne contenue dans le `CComBSTR` avant que l’objet sort de l’étendue de l’objet. Si la chaîne est libérée, le `CComBSTR` objet n’est pas valide.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#117](../atl/codesnippet/cpp/programming-with-ccombstr-atl_4.cpp)]  
  
##  <a name="programmingwithccombstr_usingloops"></a> Utilisation d’objets CComBSTR dans des boucles  
 Comme le `CComBSTR` classe alloue une mémoire tampon pour effectuer certaines opérations, telles que la `+=` opérateur ou **Append** (méthode), il est déconseillé d’effectuer de manipulation de chaînes dans une boucle étroite. Dans ces situations, `CStringT` offre de meilleures performances.  
  
### <a name="example"></a>Exemple  
 [!code-cpp[NVC_ATL_Utilities#118](../atl/codesnippet/cpp/programming-with-ccombstr-atl_5.cpp)]  
  
##  <a name="programmingwithccombstr_memoryleaks"></a> Problèmes de fuite de mémoire  
 Transmission de l’adresse d’initialisé `CComBSTR` à une fonction comme un **[out]** paramètre entraîne une fuite de mémoire.  
  
 Dans l’exemple ci-dessous, la chaîne allouée pour contenir la chaîne `"Initialized"` fuite lorsque la fonction `MyGoodFunction` remplace la chaîne.  
  
 [!code-cpp[NVC_ATL_Utilities#119](../atl/codesnippet/cpp/programming-with-ccombstr-atl_6.cpp)]  
  
 Pour éviter la fuite, appelez le **vide** méthode existant `CComBSTR` objets avant la transmission de l’adresse en tant qu’un **[out]** paramètre.  
  
 Notez que le même code ne provoque pas une fuite si le paramètre de la fonction a été **[dans, out]**.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts](../atl/active-template-library-atl-concepts.md)   
 [CStringT (classe)](../atl-mfc-shared/reference/cstringt-class.md)   
 [wstring](../standard-library/basic-string-class.md)   
 [Macros de conversion de chaînes](../atl/reference/string-conversion-macros.md)

