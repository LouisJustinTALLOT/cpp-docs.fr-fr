---
description: 'En savoir plus sur : exportation de classes de chaînes à l’aide de CStringT'
title: Exportation de classes de chaînes à l’aide de CStringT
ms.date: 11/04/2016
helpviewer_keywords:
- CStringT class, exporting strings
ms.assetid: bdfc441e-8d2a-461c-9885-46178066c09f
ms.openlocfilehash: 8876ea04f1252e4f5861a950b04dabcd99d6a804
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166991"
---
# <a name="exporting-string-classes-using-cstringt"></a>Exportation de classes de chaînes à l’aide de CStringT

Par le passé, les développeurs MFC ont dérivé de `CString` pour spécialiser leurs propres classes de chaîne. Dans Microsoft Visual C++ .NET (MFC 8,0), la classe [CString](../atl-mfc-shared/using-cstring.md) a été remplacée par une classe de modèle appelée [CStringT](../atl-mfc-shared/reference/cstringt-class.md). Cela offre plusieurs avantages :

- Elle permettait l' `CString` utilisation de la classe MFC dans les projets ATL sans lien avec la plus grande bibliothèque statique MFC ou dll.

- Avec la nouvelle `CStringT` classe de modèle, vous pouvez personnaliser le `CString` comportement à l’aide de paramètres de modèle qui spécifient des caractéristiques de caractères, comme les modèles dans la bibliothèque standard C++.

- Lorsque vous exportez votre propre classe de chaîne à partir d’une DLL à l’aide de `CStringT` , le compilateur exporte également automatiquement la `CString` classe de base. Étant donné que `CString` est lui-même une classe de modèle, il peut être instancié par le compilateur lorsqu’il est utilisé, à moins que le compilateur n’ait conscience qu’il est `CString` importé à partir d’une dll. Si vous avez migré des projets de Visual C++ 6,0 vers Visual C++ .NET, vous avez peut-être vu des erreurs de symboles de l’éditeur de liens pour un défini par multiplication en `CString` raison de la collision de l' `CString` importation à partir d’une dll et de la version instanciée localement. Pour ce faire, la méthode appropriée est décrite ci-dessous.

Le scénario suivant fait en sorte que l’éditeur de liens produise des erreurs de symbole pour les classes définies multipliées. Supposons que vous exportez une `CString` classe dérivée de ( `CMyString` ) à partir d’une DLL d’extension MFC :

[!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_1.cpp)]

Le code du consommateur utilise une combinaison de `CString` et `CMyString` . « MyString. h » n’est pas inclus dans l’en-tête précompilé, et une partie de l’utilisation de `CString` n’est pas `CMyString` visible.

Supposons que vous utilisez `CString` les `CMyString` classes et dans des fichiers sources distincts, source1. cpp et source2. cpp. Dans source1. cpp, vous utilisez `CMyString` et #include MyString. h. Dans source2. cpp, vous utilisez `CString` , mais vous ne #include pas MyString. h. Dans ce cas, l’éditeur de liens se plaint de la `CStringT` multiplication définie. Cela est dû à l' `CString` importation à partir de la dll qui exporte `CMyString` et instanciée localement par le compilateur via le `CStringT` modèle.

Pour résoudre ce problème, procédez comme suit :

Exportez `CStringA` et `CStringW` (et les classes de base nécessaires) à partir de MFC90.DLL. Les projets qui incluent MFC utilisent toujours la DLL MFC exportée `CStringA` et `CStringW` , comme dans les implémentations MFC précédentes.

Créez ensuite une classe exportable dérivée à l’aide du `CStringT` modèle, comme `CStringT_Exported` indiqué ci-dessous, par exemple :

[!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_2.cpp)]

Dans AfxStr. h, remplacez les typedefs précédents, `CString` `CStringA` et, `CStringW` comme suit :

[!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_3.cpp)]

Il existe plusieurs inconvénients :

- Vous ne devez pas exporter `CStringT` lui-même, car cela entraîne l’exportation d’une classe spécialisée par des projets ATL uniquement `CStringT` .

- L’utilisation d’une classe dérivée exportable à partir de `CStringT` minimise la nécessité d’implémenter de nouveau la `CStringT` fonctionnalité. Du code supplémentaire est limité aux constructeurs de transfert vers la `CStringT` classe de base.

- `CString`, `CStringA` et `CStringW` doivent être marqués uniquement `__declspec(dllexport/dllimport)` lorsque vous générez avec une DLL partagée MFC. Si vous établissez une liaison avec une bibliothèque statique MFC, vous ne devez pas marquer ces classes comme étant exportées ; dans le cas contraire, l’utilisation interne de `CString` , `CStringA` et `CStringW` à l’intérieur des dll utilisateur sera marquée `CString` comme étant exportée.

## <a name="related-topics"></a>Rubriques connexes

[CStringT (classe)](../atl-mfc-shared/reference/cstringt-class.md)

## <a name="see-also"></a>Voir aussi

[Utilisation de CStringT](../atl-mfc-shared/using-cstringt.md)<br/>
[Utilisation de CString](../atl-mfc-shared/using-cstring.md)
