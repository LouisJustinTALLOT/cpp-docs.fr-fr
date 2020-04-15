---
title: "Contrôles ActiveX MFC : localisation d'un contrôle ActiveX"
ms.date: 09/12/2018
f1_keywords:
- LocaleID
- AfxOleRegisterTypeLib
helpviewer_keywords:
- localization, ActiveX controls
- MFC ActiveX controls [MFC], localizing
- LocaleID ambient property [MFC]
- LOCALIZE sample [MFC]
ms.assetid: a44b839a-c652-4ec5-b824-04392708a5f9
ms.openlocfilehash: 987cde2117307cdb5940a31e6f01efb15c527b84
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364595"
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>Contrôles ActiveX MFC : localisation d'un contrôle ActiveX

Cet article décrit les procédures permettant de rechercher des interfaces de contrôle ActiveX.

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, voir [ActiveX Controls](activex-controls.md).

Si vous souhaitez adapter un contrôle ActiveX à un marché international, vous pouvez le localiser. Windows prend en charge plusieurs langues en plus de l'anglais par défaut, notamment l'allemand, le français et le suédois. Cela peut présenter des problèmes pour le contrôle si l'interface est uniquement en anglais.

En général, les contrôles ActiveX doivent toujours être basés sur les paramètres régionaux de la propriété LocaleID ambiante. Pour ce faire, deux possibilités s'offrent à vous :

- Chargez les ressources, toujours à la demande, en fonction de la valeur actuelle de la propriété LocaleID ambiante. L’échantillon de contrôle MFC ActiveX [LOCALIZE](../overview/visual-cpp-samples.md) utilise cette stratégie.

- Chargez les ressources lorsque le premier contrôle est instancié, selon la propriété LocaleID ambiante, et utilisez ces ressources pour toutes les autres instances. Cet article explique cette stratégie.

    > [!NOTE]
    >  Cela ne fonctionne pas correctement dans certains cas, lorsque les instances ont des paramètres régionaux.

- Utilisez `OnAmbientChanged` la fonction de notification pour charger dynamiquement les ressources appropriées pour le lieu du conteneur.

    > [!NOTE]
    >  Cela fonctionne pour le contrôle, mais la DLL d'exécution ne met pas à jour dynamiquement ses propres ressources lorsque la propriété LocaleID ambiante change. En outre, les DLL d'exécution des contrôles ActiveX utilisent les paramètres régionaux du thread pour déterminer les paramètres régionaux pour ses ressources.

Le reste de cet article décrit deux stratégies localisantes. La première stratégie [localise l’interface de programmabilité du contrôle](#_core_localizing_your_control.92.s_programmability_interface) (noms des propriétés, des méthodes et des événements). La deuxième stratégie [localise l’interface utilisateur du contrôle,](#_core_localizing_the_control.92.s_user_interface)en utilisant la propriété localeID ambiante du conteneur. Pour une démonstration de localisation de contrôle, voir l’échantillon de contrôles MFC ActiveX [LOCALIZE](../overview/visual-cpp-samples.md).

## <a name="localizing-the-controls-programmability-interface"></a><a name="_core_localizing_your_control.92.s_programmability_interface"></a>Localisation de l’interface de programmabilité du Contrôle

En recherchant l'interface de programmabilité du contrôle (l'interface utilisée par les programmeurs dans les applications qui utilisent votre contrôle), vous devez créer une version modifiée du fichier .IDL de contrôle (un script pour générer la bibliothèque de types de contrôle) pour chaque langue que vous envisagez de prendre en charge. Il s'agit du seul emplacement dont vous avez besoin pour localiser les noms de propriété de contrôle.

Lorsque vous développez un contrôle localisé, incluez l'ID de paramètres régionaux comme attribut au niveau de la bibliothèque de types. Par exemple, si vous souhaitez fournir une bibliothèque de types avec des noms de propriété localisés en français, créez une copie du fichier SAMPLE.IDL et appelez-la SAMPLEFR.IDL. Ajoutez un attribut ID de paramètres régionaux au fichier (l'ID de paramètres régionaux pour le français est 0x040c), comme suit :

[!code-cpp[NVC_MFC_AxLoc#1](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]

Remplacez les noms des propriétés dans le fichier SAMPLEFR.IDL par leurs équivalents français, puis utilisez le fichier MKTYPLIB.EXE pour produire la bibliothèque de types française, SAMPLEFR.TLB.

Pour créer plusieurs bibliothèques de types traduites, vous pouvez ajouter au projet des fichiers .IDL localisés pour qu'ils soient générés automatiquement.

#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>Pour ajouter un fichier .IDL à votre projet de contrôle ActiveX

1. Avec votre projet de contrôle ouvert, sur le menu du **projet,** cliquez sur **Ajouter l’élément existant**.

   La boîte de dialogue **d’élément existant d’ajouter** apparaît.

1. Si nécessaire, sélectionnez le lecteur et le répertoire à afficher.

1. Dans la boîte **de fichiers de type,** sélectionnez **tous les fichiers (\*.\*. . .**

1. Dans la zone de liste de fichiers, double-cliquez sur le fichier .IDL que vous souhaitez insérer dans le projet.

1. Cliquez **sur Ouvrez** lorsque vous avez ajouté tous les nécessaires . Fichiers IDL.

Les fichiers ont été ajoutés au projet, ils seront générés lorsque le reste du projet sera généré. Les bibliothèques de types localisées se trouvent dans le répertoire du projet du contrôle ActiveX actuel.

Dans votre code, les noms des propriétés internes (généralement en anglais) sont toujours utilisés et ne sont jamais localisés. Cela inclut la table de dispatch de contrôle, les fonctions d'échange de propriété et votre code d'échange de données de page de propriétés.

Un seul fichier de bibliothèque de types (.TLB) peut être lié aux ressources du fichier d'implémentation de contrôle (.OCX). Il s'agit souvent de la version avec les noms standardisés (généralement en anglais). Pour fournir une version localisée de votre contrôle, vous devez fournir le fichier .OCX (qui est déjà lié à la version .TLB par défaut) et le fichier .TLB pour les paramètres régionaux appropriés. Cela signifie que le fichier .OCX est nécessaire pour les versions en anglais, puisque le fichier .TLB approprié est déjà lié à celui-ci. Pour les autres paramètres régionaux, la bibliothèque de types localisée doit être fournie avec le fichier .OCX.

Pour vérifier que les clients de votre contrôle peuvent localiser la bibliothèque de types localisée, inscrivez vos fichiers .TLB spécifiques aux paramètres régionaux sous la section TypeLib du Registre système Windows. Le troisième paramètre (normalement facultatif) de la fonction [AfxOleRegisterTypeLib](../mfc/reference/registering-ole-controls.md#afxoleregistertypelib) est fourni à cette fin. L'exemple suivant inscrit une bibliothèque de types française pour un contrôle ActiveX :

[!code-cpp[NVC_MFC_AxLoc#2](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]

Lorsque votre contrôle est inscrit, la fonction `AfxOleRegisterTypeLib` recherche automatiquement le fichier .TLB spécifié dans le même répertoire que le contrôle et l'inscrit dans la base de données d'inscription de Windows. Si le fichier .TLB est introuvable, la fonction n'a aucun effet.

## <a name="localizing-the-controls-user-interface"></a><a name="_core_localizing_the_control.92.s_user_interface"></a>Localisation de l’interface utilisateur du contrôle

Pour rechercher l'interface utilisateur d'un contrôle, placez toutes les ressources accessibles à l'utilisateur du contrôle (telles que les pages de propriétés et les messages d'erreur) dans les DLL de ressource spécifiques aux langues. Vous pouvez utiliser la propriété LocaleID ambiante du conteneur pour sélectionner la DLL appropriée pour les paramètres régionaux de l'utilisateur.

L'exemple de code suivant illustre une approche pour localiser et charger la DLL de ressource pour les paramètres régionaux spécifiques. Cette fonction membre, appelée `GetLocalizedResourceHandle` dans cet exemple, peut être une fonction membre de la classe de contrôle ActiveX :

[!code-cpp[NVC_MFC_AxLoc#3](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]

Notez que l'ID de sous-langue peut être activé dans chaque cas d'instruction switch, pour fournir plus de localisation spécialisée. Pour une démonstration de cette `GetResourceHandle` fonction, voir la fonction dans l’échantillon de contrôles MFC ActiveX [LOCALIZE](../overview/visual-cpp-samples.md).

Lorsque le contrôle se charge pour la première fois dans un conteneur, il peut appeler [COleControl::AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid) pour récupérer l’ID local. Le contrôle peut ensuite passer la valeur retournée de l'ID des paramètres régionaux à la fonction `GetLocalizedResourceHandle`, qui charge la bibliothèque de ressources appropriée. Le contrôle doit passer la poignée résultante, le cas échéant, à [AfxSetResourceHandle](../mfc/reference/application-information-and-management.md#afxsetresourcehandle):

[!code-cpp[NVC_MFC_AxLoc#4](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]

Placez l’échantillon de code ci-dessus dans une fonction membre du contrôle, comme un remplacement de [COleControl::OnSetClientSite](../mfc/reference/colecontrol-class.md#onsetclientsite). En outre, *m_hResDLL* devrait être une variable membre de la classe de contrôle.

Vous pouvez utiliser une logique similaire pour localiser la page des propriétés d'un contrôle. Pour localiser la page de propriété, ajoutez du code similaire à l’échantillon suivant au fichier d’implémentation de votre page de propriété (dans un remplacement de [COlePropertyPage::OnSetPageSite)](../mfc/reference/colepropertypage-class.md#onsetpagesite):

[!code-cpp[NVC_MFC_AxLoc#5](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)
