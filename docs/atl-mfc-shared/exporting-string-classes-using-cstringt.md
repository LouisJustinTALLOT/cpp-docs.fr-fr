---
title: Exporter des Classes de chaîne à l’aide de CStringT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CStringT class, exporting strings
ms.assetid: bdfc441e-8d2a-461c-9885-46178066c09f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5355b6e81354ef04b7cc4d2c3495289c9d1d029d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444202"
---
# <a name="exporting-string-classes-using-cstringt"></a>Exporter des Classes de chaîne à l’aide de CStringT

Dans le passé, les développeurs MFC ont dérivé `CString` pour spécialiser leurs propres classes de chaîne. Dans Microsoft Visual C++ .NET (MFC 8.0), le [CString](../atl-mfc-shared/using-cstring.md) classe a été remplacée par une classe de modèle nommée [CStringT](../atl-mfc-shared/reference/cstringt-class.md). Cela fourni plusieurs avantages :

- Il autorisé MFC `CString` classe à utiliser dans les ATL projets sans liaison dans la plus grande bibliothèque statique MFC ou une DLL.

- Avec la nouvelle `CStringT` classe de modèle, vous pouvez personnaliser `CString` comportement à l’aide des paramètres de modèle qui spécifient les caractéristiques de caractère, similaires aux modèles dans la bibliothèque C++ Standard.

- Lorsque vous exportez votre propre classe de chaîne à partir d’une DLL à l’aide `CStringT`, le compilateur exporte également automatiquement la `CString` classe de base. Dans la mesure où `CString` lui-même est une classe de modèle, elle peut être instanciée par le compilateur lorsqu’il est utilisé, à moins que le compilateur connaît qui `CString` est importée à partir d’une DLL. Si vous avez migré des projets à partir de Visual C++ 6.0 vers Visual C++ .NET, vous avez peut-être vu des erreurs de symbole de l’éditeur de liens pour un défini à plusieurs reprises `CString` en raison de la collision de la `CString` importées à partir d’une DLL et la version instanciée localement. La méthode appropriée pour ce faire est décrite ci-dessous. Pour plus d’informations sur ce problème, consultez l’article de la Base de connaissances, « erreurs de liaison lorsque vous importez des dérivées de CString Classes » (Q309801) à [ http://support.microsoft.com/default.aspx ](http://support.microsoft.com/default.aspx).

Le scénario suivant entraîne l’éditeur de liens produire des erreurs de symboles pour les classes définis à plusieurs reprises. Supposons que vous exportez un `CString`-classe dérivée (`CMyString`) à partir d’une DLL d’extension MFC :

[!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_1.cpp)]

Le code de consommateur utilise un mélange de `CString` et `CMyString`. « MyString.h » n’est pas inclus dans l’en-tête précompilé et certains l’utilisation de `CString` n’a pas `CMyString` visible.

Supposons que vous utilisez le `CString` et `CMyString` classes dans des fichiers sources distincts, Source1.cpp et Source2.cpp. Dans Source1.cpp, vous utilisez `CMyString` et #include MyString.h. Dans Source2.cpp, vous utilisez `CString`, mais ne le faites pas #include MyString.h. Dans ce cas, l’éditeur de liens se plaindront sur `CStringT` qui est défini plusieurs fois. Cela est dû au fait `CString` étant toutes deux été importées à partir de la DLL qui exporte `CMyString`et instancié localement par le compilateur via la `CStringT` modèle.

Pour résoudre ce problème, procédez comme suit :

Exporter `CStringA` et `CStringW` (et les classes de base nécessaires) à partir de MFC90. DLL. Les projets qui incluent des MFC utilisent toujours la DLL de MFC exportée `CStringA` et `CStringW`, comme dans les implémentations précédentes de MFC.

Puis créez une classe dérivée exportable à l’aide de la `CStringT` modèle, en tant que `CStringT_Exported` est indiquée ci-dessous, par exemple :

[!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_2.cpp)]

Dans AfxStr.h, remplacez le précédent `CString`, `CStringA`, et `CStringW` typedefs comme suit :

[!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_3.cpp)]

Il existe plusieurs inconvénients :

- Vous ne devez pas exporter `CStringT` lui-même, car cela entraîne des projets ATL seule exportation spécialisé `CStringT` classe.

- À l’aide d’un exportable dérivé de classe de `CStringT` réduit de devoir réimplémenter `CStringT` fonctionnalité. Code supplémentaire est limité au transfert des constructeurs pour la `CStringT` classe de base.

- `CString`, `CStringA`, et `CStringW` doit uniquement être marquée `__declspec(dllexport/dllimport)` lorsque vous générez une MFC DLL partagée. Si une liaison avec une bibliothèque statique MFC, vous ne devez pas marquer ces classes comme l’exportation ; utilisation interne et sinon de `CString`, `CStringA`, et `CStringW` marque à l’intérieur de l’utilisateur DLL `CString` comme exportés également.

## <a name="related-topics"></a>Rubriques connexes

[CStringT, classe](../atl-mfc-shared/reference/cstringt-class.md)

## <a name="see-also"></a>Voir aussi

[Utilisation de CStringT](../atl-mfc-shared/using-cstringt.md)<br/>
[Utilisation de CString](../atl-mfc-shared/using-cstring.md)

