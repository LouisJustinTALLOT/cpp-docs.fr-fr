---
title: 'Contrôles ActiveX MFC : Localisation d’un contrôle ActiveX | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- LocaleID
- AfxOleRegisterTypeLib
dev_langs:
- C++
helpviewer_keywords:
- localization, ActiveX controls
- MFC ActiveX controls [MFC], localizing
- LocaleID ambient property [MFC]
- LOCALIZE sample [MFC]
ms.assetid: a44b839a-c652-4ec5-b824-04392708a5f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b9a6495c23695f8cdedf45fbdd7cbc915b96873e
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929606"
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>Contrôles ActiveX MFC : localisation d'un contrôle ActiveX
Cet article décrit les procédures permettant de rechercher des interfaces de contrôle ActiveX.  
  
 Si vous souhaitez adapter un contrôle ActiveX à un marché international, vous pouvez le localiser. Windows prend en charge plusieurs langues en plus de l'anglais par défaut, notamment l'allemand, le français et le suédois. Cela peut présenter des problèmes pour le contrôle si l'interface est uniquement en anglais.  
  
 En général, les contrôles ActiveX doivent toujours être basés sur les paramètres régionaux de la propriété LocaleID ambiante. Il y a trois manières pour effectuer cette opération :  
  
-   Chargez les ressources, toujours à la demande, en fonction de la valeur actuelle de la propriété LocaleID ambiante. Exemple de contrôles ActiveX MFC [LOCALIZE](../visual-cpp-samples.md) utilise cette stratégie.  
  
-   Chargez les ressources lorsque le premier contrôle est instancié, selon la propriété LocaleID ambiante, et utilisez ces ressources pour toutes les autres instances. Cet article explique cette stratégie.  
  
    > [!NOTE]
    >  Cela ne fonctionne pas correctement dans certains cas, lorsque les instances ont des paramètres régionaux.  
  
-   Utilisez le `OnAmbientChanged` fonction de notification pour charger dynamiquement les ressources appropriées pour des paramètres régionaux du conteneur.  
  
    > [!NOTE]
    >  Cela fonctionne pour le contrôle, mais la DLL d'exécution ne met pas à jour dynamiquement ses propres ressources lorsque la propriété LocaleID ambiante change. En outre, les DLL d’exécution des contrôles ActiveX utilisent les paramètres régionaux du thread pour déterminer les paramètres régionaux pour ses ressources.  
  
 Le reste de cet article décrit deux stratégies localisantes. La première stratégie [localise l’interface de programmabilité du contrôle](#_core_localizing_your_control.92.s_programmability_interface) (noms des propriétés, méthodes et événements). La seconde stratégie [localise l’interface utilisateur du contrôle](#_core_localizing_the_control.92.s_user_interface), à l’aide de la propriété de LocaleID ambiante du conteneur. Pour une démonstration de la localisation de contrôle, consultez l’exemple de contrôles ActiveX MFC [LOCALIZE](../visual-cpp-samples.md).  
  
##  <a name="_core_localizing_your_control.92.s_programmability_interface"></a> Localisation d’Interface de programmabilité du contrôle  
 En recherchant l'interface de programmabilité du contrôle (l'interface utilisée par les programmeurs dans les applications qui utilisent votre contrôle), vous devez créer une version modifiée du fichier .IDL de contrôle (un script pour générer la bibliothèque de types de contrôle) pour chaque langue que vous envisagez de prendre en charge. Il s'agit du seul emplacement dont vous avez besoin pour localiser les noms de propriété de contrôle.  
  
 Lorsque vous développez un contrôle localisé, incluez l'ID de paramètres régionaux comme attribut au niveau de la bibliothèque de types. Par exemple, si vous souhaitez fournir une bibliothèque de types avec des noms de propriété localisés en français, créez une copie du fichier SAMPLE.IDL et appelez-la SAMPLEFR.IDL. Ajoutez un attribut ID de paramètres régionaux au fichier (l'ID de paramètres régionaux pour le français est 0x040c), comme suit :  
  
 [!code-cpp[NVC_MFC_AxLoc#1](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]  
  
 Remplacez les noms des propriétés dans le fichier SAMPLEFR.IDL par leurs équivalents français, puis utilisez le fichier MKTYPLIB.EXE pour produire la bibliothèque de types française, SAMPLEFR.TLB.  
  
 Pour créer plusieurs bibliothèques de types traduites, vous pouvez ajouter au projet des fichiers .IDL localisés pour qu'ils soient générés automatiquement.  
  
#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>Pour ajouter un fichier .IDL à votre projet de contrôle ActiveX  
  
1.  Avec votre projet de contrôle ouvert, dans le **projet** menu, cliquez sur **ajouter un élément existant**.  
  
     Le **ajouter un élément existant** boîte de dialogue s’affiche.  
  
2.  Si nécessaire, sélectionnez le lecteur et le répertoire à afficher.  
  
3.  Dans le **types de fichiers** boîte, sélectionnez **tous les fichiers (\*.\*)** .  
  
4.  Dans la zone de liste de fichiers, double-cliquez sur le fichier .IDL que vous souhaitez insérer dans le projet.  
  
5.  Cliquez sur **ouvrir** lorsque vous avez ajouté tous les fichiers. Fichiers IDL.  
  
 Les fichiers ont été ajoutés au projet, ils seront générés lorsque le reste du projet sera généré. Les bibliothèques de types localisées se trouvent dans le répertoire du projet du contrôle ActiveX actuel.  
  
 Dans votre code, les noms des propriétés internes (généralement en anglais) sont toujours utilisés et ne sont jamais localisés. Cela inclut la table de dispatch de contrôle, les fonctions d'échange de propriété et votre code d'échange de données de page de propriétés.  
  
 Un seul fichier de bibliothèque de types (.TLB) peut être lié aux ressources du fichier d'implémentation de contrôle (.OCX). Il s'agit souvent de la version avec les noms standardisés (généralement en anglais). Pour fournir une version localisée de votre contrôle, vous devez fournir le fichier .OCX (qui est déjà lié à la version .TLB par défaut) et le fichier .TLB pour les paramètres régionaux appropriés. Cela signifie que le fichier .OCX est nécessaire pour les versions en anglais, puisque le fichier .TLB approprié est déjà lié à celui-ci. Pour les autres paramètres régionaux, la bibliothèque de types localisée doit être fournie avec le fichier .OCX.  
  
 Pour vérifier que les clients de votre contrôle peuvent localiser la bibliothèque de types localisée, inscrivez vos fichiers .TLB spécifiques aux paramètres régionaux sous la section TypeLib du Registre système Windows. Le troisième paramètre (normalement facultatif) de la [AfxOleRegisterTypeLib](../mfc/reference/registering-ole-controls.md#afxoleregistertypelib) fonction est fournie à cet effet. L'exemple suivant inscrit une bibliothèque de types française pour un contrôle ActiveX :  
  
 [!code-cpp[NVC_MFC_AxLoc#2](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]  
  
 Lorsque votre contrôle est inscrit, la fonction `AfxOleRegisterTypeLib` recherche automatiquement le fichier .TLB spécifié dans le même répertoire que le contrôle et l'inscrit dans la base de données d'inscription de Windows. Si le fichier .TLB est introuvable, la fonction n'a aucun effet.  
  
##  <a name="_core_localizing_the_control.92.s_user_interface"></a> Localisation de l’Interface du contrôle utilisateur  
 Pour rechercher l'interface utilisateur d'un contrôle, placez toutes les ressources accessibles à l'utilisateur du contrôle (telles que les pages de propriétés et les messages d'erreur) dans les DLL de ressource spécifiques aux langues. Vous pouvez utiliser la propriété LocaleID ambiante du conteneur pour sélectionner la DLL appropriée pour les paramètres régionaux de l'utilisateur.  
  
 L'exemple de code suivant illustre une approche pour localiser et charger la DLL de ressource pour les paramètres régionaux spécifiques. Cette fonction membre, appelée `GetLocalizedResourceHandle` dans cet exemple, peut être une fonction membre de la classe de contrôle ActiveX :  
  
 [!code-cpp[NVC_MFC_AxLoc#3](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]  
  
 Notez que l'ID de sous-langue peut être activé dans chaque cas d'instruction switch, pour fournir plus de localisation spécialisée. Pour une démonstration de cette fonction, consultez le `GetResourceHandle` exemple de contrôles de fonction dans les MFC ActiveX [LOCALIZE](../visual-cpp-samples.md).  
  
 Lorsque le premier contrôle se charge dans un conteneur, il peut appeler [COleControl::AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid) pour récupérer l’ID de paramètres régionaux. Le contrôle peut ensuite passer la valeur retournée de l'ID des paramètres régionaux à la fonction `GetLocalizedResourceHandle`, qui charge la bibliothèque de ressources appropriée. Le contrôle doit passer le handle obtenu, si elle existe, à [AfxSetResourceHandle](../mfc/reference/application-information-and-management.md#afxsetresourcehandle):  
  
 [!code-cpp[NVC_MFC_AxLoc#4](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]  
  
 Placez l’exemple de code ci-dessus dans une fonction membre du contrôle, tel qu’un remplacement de [COleControl::OnSetClientSite](../mfc/reference/colecontrol-class.md#onsetclientsite). En outre, *m_hResDLL* doit être une variable membre de la classe du contrôle.  
  
 Vous pouvez utiliser une logique similaire pour localiser la page des propriétés d'un contrôle. Pour localiser la page de propriétés, ajoutez un code similaire à l’exemple suivant au fichier d’implémentation de la page de propriétés (dans une substitution de [COlePropertyPage::OnSetPageSite](../mfc/reference/colepropertypage-class.md#onsetpagesite)) :  
  
 [!code-cpp[NVC_MFC_AxLoc#5](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)

