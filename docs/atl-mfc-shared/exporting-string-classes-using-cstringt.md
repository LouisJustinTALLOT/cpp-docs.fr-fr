---
title: Exporter des Classes de chaîne à l’aide de CStringT | Documents Microsoft
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
ms.openlocfilehash: 7510b1f44f49d17211c71419f4dde5a6e6a78974
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356394"
---
# <a name="exporting-string-classes-using-cstringt"></a>Exporter des Classes de chaîne à l’aide de CStringT
Dans le passé, les développeurs MFC ont dérivé `CString` pour spécialiser leurs propres classes de chaîne. Dans Microsoft Visual C++ .NET (MFC 8.0), la [CString](../atl-mfc-shared/using-cstring.md) classe a été remplacée par une classe de modèle appelée [CStringT](../atl-mfc-shared/reference/cstringt-class.md). Cette condition présente plusieurs avantages :  
  
-   Est-il possible de la bibliothèque MFC `CString` projets de classe à utiliser dans les ATL sans établir de liaison dans la plus grande bibliothèque statique MFC ou une DLL.  
  
-   Avec la nouvelle `CStringT` classe de modèle, vous pouvez personnaliser `CString` comportement à l’aide des paramètres de modèle qui spécifient les caractéristiques, similaires aux modèles dans la bibliothèque C++ Standard.  
  
-   Lorsque vous exportez votre propre classe de chaîne à partir d’une DLL à l’aide `CStringT`, le compilateur exporte également automatiquement le `CString` classe de base. Étant donné que `CString` lui-même est une classe de modèle, il peut être instancié par le compilateur lorsqu’il est utilisé, à moins que le compilateur connaît qui `CString` est importée à partir d’une DLL. Si vous avez migré des projets à partir de Visual C++ 6.0 vers Visual C++ .NET, vous pouvez vu erreurs de symbole de l’éditeur de liens pour un défini à plusieurs reprises `CString` en raison de la collision de la `CString` importées à partir d’une DLL et de la version instanciée localement. La méthode appropriée pour cela est décrit ci-dessous. Pour plus d’informations sur ce problème, consultez l’article de la Base de connaissances, « erreurs de liaison lorsque vous importez dérivée CString Classes » (Q309801) à [ http://support.microsoft.com/default.aspx ](http://support.microsoft.com/default.aspx).  
  
 Le scénario suivant entraînera l’éditeur de liens générer des erreurs de symbole pour les classes définis à plusieurs reprises. Supposons que vous exportez un `CString`-classe dérivée (`CMyString`) à partir d’une DLL d’extension MFC :  
  
 [!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_1.cpp)]  
  
 Le code de consommateur utilise un mélange de `CString` et `CMyString`. « MyString.h » n’est pas inclus dans l’en-tête précompilé et certains d’utilisation de `CString` n’a pas `CMyString` visible.  
  
 Supposons que vous utilisez le `CString` et `CMyString` classes dans les fichiers source séparée, Source1.cpp et Source2.cpp. Dans Source1.cpp, vous utilisez `CMyString` et #include MyString.h. Dans Source2.cpp, vous utilisez `CString`, mais pas les #include MyString.h. Dans ce cas, l’éditeur de liens sera contester `CStringT` qui est défini plusieurs fois. Cela est dû au fait `CString` étant toutes deux été importées à partir de la DLL qui exporte `CMyString`et instanciés localement par le compilateur via la `CStringT` modèle.  
  
 Pour résoudre ce problème, procédez comme suit :  
  
 Exporter `CStringA` et `CStringW` (et les classes de base nécessaires) à partir de MFC90. DLL. Les projets qui incluent les MFC utilisent toujours la DLL MFC exportée `CStringA` et `CStringW`, comme dans les implémentations précédentes de MFC.  
  
 Puis créer une classe dérivée exportable à l’aide de la `CStringT` modèle, en tant que `CStringT_Exported` est inférieur, par exemple :  
  
 [!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_2.cpp)]  
  
 Dans AfxStr.h, remplacez le texte précédent `CString`, `CStringA`, et `CStringW` typedefs comme suit :  
  
 [!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_3.cpp)]  
  
 Il existe plusieurs points à noter :  
  
-   Vous ne devez pas exporter `CStringT` lui-même, car cela entraîne les projets ATL seule exportation spécialisé `CStringT` classe.  
  
-   À l’aide d’un exportable dérivé de classe de `CStringT` réduit de devoir réimplémenter `CStringT` fonctionnalité. Code supplémentaire est limité à des constructeurs de transfert la `CStringT` classe de base.  
  
-   `CString`, `CStringA`, et `CStringW` doit uniquement être marquée `__declspec(dllexport/dllimport)` lorsque vous générez une MFC DLL partagée. Si une liaison avec une bibliothèque statique MFC, vous ne devez pas marquer ces classes exportées ; Sinon, interne utilisation de `CString`, `CStringA`, et `CStringW` marque à l’intérieur de l’utilisateur DLL `CString` comme exportés également.  
  
## <a name="related-topics"></a>Rubriques connexes  
 [CStringT, classe](../atl-mfc-shared/reference/cstringt-class.md)  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de CStringT](../atl-mfc-shared/using-cstringt.md)   
 [Utilisation de CString](../atl-mfc-shared/using-cstring.md)

