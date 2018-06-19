---
title: 'Contrôles ActiveX MFC : Licences des contrôles ActiveX | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- COleObjectFactory
dev_langs:
- C++
helpviewer_keywords:
- COleObjectFactory class [MFC], licensing controls
- MFC ActiveX controls [MFC], licensing
- VerifyLicenseKey method [MFC]
- VerifyUserLicense method [MFC]
- GetLicenseKey method [MFC]
- licensing ActiveX controls
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 725e6cf167ec01635a3072f09ecaa2f5055b1891
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353924"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>Contrôles ActiveX MFC : gestion des licences d'un contrôle ActiveX
Prise en charge de licences, une fonctionnalité facultative de contrôles ActiveX, vous permet de contrôler qui peut utiliser ou distribuer le contrôle. (Pour davantage d’informations sur les problèmes de gestion de licences, consultez les problèmes de gestion de licences dans [mise à niveau d’un contrôle ActiveX](../mfc/upgrading-an-existing-activex-control.md).)  
  
 Cet article traite des sujets suivants :  
  
-   [Vue d’ensemble du contrôle ActiveX de licence](#_core_overview_of_activex_control_licensing)  
  
-   [Création d’un contrôle sous licence](#_core_creating_a_licensed_control)  
  
-   [Prise en charge](#_core_licensing_support)  
  
-   [Personnalisation de la gestion des licences d’un contrôle ActiveX](#_core_customizing_the_licensing_of_an_activex_control)  
  
 Contrôles ActiveX qui implémentent des licences vous permettent, en tant que le développeur du contrôle, pour déterminer la façon dont les autres personnes utiliseront le contrôle ActiveX. Vous fournissez à l’acheteur avec le contrôle et. LIC avec l’accord que l’acheteur peut distribuer le contrôle, mais pas le. LIC avec une application qui utilise le contrôle. Cela empêche les utilisateurs de l’application à partir de l’écriture de nouvelles applications qui utilisent le contrôle, sans le premier gestionnaire de licences du contrôle de votre part.  
  
##  <a name="_core_overview_of_activex_control_licensing"></a> Vue d’ensemble du contrôle ActiveX de licence  
 Pour prendre en charge licences des contrôles ActiveX, la [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) classe fournit une implémentation de plusieurs fonctions dans le **IClassFactory2** interface : **IClassFactory2 :: RequestLicKey**, **IClassFactory2::GetLicInfo**, et **IClassFactory2::CreateInstanceLic**. Lorsque le développeur d’applications conteneur effectue une demande pour créer une instance du contrôle, un appel à `GetLicInfo` est effectuée pour vérifier que le contrôle. LIC fichier est présent. Si le contrôle est concédé sous licence, une instance du contrôle peut être créée et placée dans le conteneur. Une fois que le développeur a terminé la construction de l’application conteneur, un autre appel de fonction, cette fois-ci pour `RequestLicKey`, est effectuée. Cette fonction retourne une clé de licence (une simple chaîne de caractères) à l’application conteneur. La clé retournée est ensuite incorporée dans l’application.  
  
 La figure ci-dessous illustre la vérification de la licence d’un contrôle ActiveX qui sera utilisé pendant le développement d’une application conteneur. Comme mentionné précédemment, le développeur d’applications de conteneur doit avoir la bonne. LIC approprié sur l’ordinateur de développement pour créer une instance du contrôle.  
  
 ![Contrôle ActiveX vérifié au développement d’une licence](../mfc/media/vc374d1.gif "vc374d1")  
Vérification d’un contrôle ActiveX sous licence pendant le développement  
  
 Le processus suivant, illustré dans l’illustration suivante, se produit lorsque l’utilisateur final exécute l’application conteneur.  
  
 Lorsque l’application est lancée, une instance du contrôle doit généralement être créée. Le conteneur cela apporte un appel à `CreateInstanceLic`, en passant de la clé de licence incorporée en tant que paramètre. Une comparaison de chaînes est ensuite effectuée entre la clé de licence incorporée et la copie du contrôle de la clé de licence. Si la correspondance est réussie, une instance du contrôle est créée et l’application continue de s’exécuter normalement. Notez que le. Fichier LIC ne sont pas nécessairement présent sur l’ordinateur de l’utilisateur contrôle.  
  
 ![Contrôle ActiveX vérifié au moment de l’exécution d’une licence](../mfc/media/vc374d2.gif "vc374d2")  
Vérification d’un contrôle ActiveX sous licence pendant l’exécution  
  
 Licences de contrôles se compose de deux composants de base : un code spécifique dans la DLL d’implémentation du contrôle et le fichier de licence. Le code est composé de deux (ou trois éventuellement) des appels de fonction et d’une chaîne de caractères, ci-après dénommé « chaîne de licence », qui contient une mention de copyright. Ces appels et la chaîne de licence sont trouvent dans l’implémentation du contrôle (. (CPP) du contrôle. Le fichier de licence, généré par l’Assistant contrôle ActiveX, est un fichier texte avec une déclaration de copyright. Il est nommé en utilisant le nom de projet avec un. LIC, par exemple SAMPLE. CONTRAT DE LICENCE De. Si vous avez besoin des utiliser au moment du design, un contrôle sous licence doit être accompagné par le fichier de licence.  
  
##  <a name="_core_creating_a_licensed_control"></a> Création d’un contrôle sous licence  
 Lorsque vous utilisez l’Assistant contrôle ActiveX pour créer l’infrastructure de contrôle, il est facile d’inclure la prise en charge. Lorsque vous spécifiez que le contrôle doit avoir une licence d’exécution, l’Assistant contrôle ActiveX ajoute le code à la classe de contrôle pour prendre en charge le Gestionnaire de licences. Le code se compose de fonctions qui utilisent un fichier de clé et la licence pour la vérification de la licence. Ces fonctions peuvent également être modifiées pour personnaliser la licence du contrôle. Pour plus d’informations sur la personnalisation des licences, consultez [personnalisation de la licence d’un contrôle ActiveX](#_core_customizing_the_licensing_of_an_activex_control) plus loin dans cet article.  
  
#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>Pour ajouter la prise en charge des licences par l’Assistant contrôle ActiveX lorsque vous créez votre projet de contrôle  
  
1.  Suivez les instructions de [création d’un contrôle ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md). Le **paramètres de l’Application** page de l’Assistant contrôle ActiveX contient l’option pour créer le contrôle avec la licence d’exécution.  
  
 L’Assistant contrôle ActiveX génère maintenant une infrastructure de contrôle ActiveX qui inclut la prise en charge licences élémentaire. Pour obtenir une explication détaillée du code de gestion des licences, consultez la rubrique suivante.  
  
##  <a name="_core_licensing_support"></a> Prise en charge  
 Lorsque vous utilisez l’Assistant contrôle ActiveX pour ajouter la prise en charge licences à un contrôle ActiveX, l’Assistant contrôle ActiveX ajoute le code qui déclare et implémente la fonction de licence est ajouté à l’en-tête de contrôle et l’implémentation de fichiers. Ce code est composé d’un `VerifyUserLicense` fonction membre et un `GetLicenseKey` fonction membre, qui remplacent les implémentations par défaut trouvées dans [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) . Ces fonctions récupèrent et vérifiez que la licence du contrôle.  
  
> [!NOTE]
>  Une troisième fonction membre, `VerifyLicenseKey` n’est pas généré par l’Assistant contrôle ActiveX, mais peut être substituée pour personnaliser le comportement de vérification de la clé de licence.  
  
 Ces fonctions membres sont :  
  
-   [VerifyUserLicense](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)  
  
     Vérifie que le contrôle permet une utilisation au moment du design en vérifiant le système la présence du fichier de licence du contrôle. Cette fonction est appelée par l’infrastructure en tant que partie du traitement **IClassFactory2::GetLicInfo** et **IClassFactory::CreateInstanceLic**.  
  
-   [GetLicenseKey](../mfc/reference/coleobjectfactory-class.md#getlicensekey)  
  
     Demande une clé unique à partir de la DLL du contrôle. Cette clé est incorporée dans l’application conteneur et utilisée avec une version ultérieure, `VerifyLicenseKey`, pour créer une instance du contrôle. Cette fonction est appelée par l’infrastructure en tant que partie du traitement **IClassFactory2::RequestLicKey**.  
  
-   [VerifyLicenseKey](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)  
  
     Vérifie que les clés incorporées et unique du contrôle sont identiques. Ainsi, le conteneur créer une instance du contrôle pour son utilisation. Cette fonction est appelée par l’infrastructure en tant que partie du traitement **IClassFactory2::CreateInstanceLic** et peut être substituée pour fournir une vérification personnalisée de la clé de licence. L’implémentation par défaut effectue une comparaison de chaînes. Pour plus d’informations, consultez [personnalisation de la licence d’un contrôle ActiveX](#_core_customizing_the_licensing_of_an_activex_control), plus loin dans cet article.  
  
###  <a name="_core_header_file_modifications"></a> Modifications de fichier d’en-tête  
 L’Assistant contrôle ActiveX place le code suivant dans le fichier d’en-tête. Dans cet exemple, deux fonctions membres de `CSampleCtrl`de l’objet `factory` sont déclarés, l’autre qui vérifie la présence du contrôle. LIC de fichiers et une autre qui extrait la clé de licence à utiliser dans l’application contenant le contrôle :  
  
 [!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]  
  
###  <a name="_core_implementation_file_modifications"></a> Modifications de fichier d’implémentation  
 L’Assistant contrôle ActiveX place les deux instructions suivantes dans le fichier d’implémentation pour déclarer le nom de fichier de licence et la chaîne de licence :  
  
 [!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]  
  
> [!NOTE]
>  Si vous modifiez **szLicString** de quelque façon, vous devez également modifier la première ligne dans le contrôle. Fichier LIC ou le Gestionnaire de licences ne fonctionnera pas correctement.  
  
 L’Assistant contrôle ActiveX place le code suivant dans le fichier d’implémentation pour définir la classe du contrôle `VerifyUserLicense` et `GetLicenseKey` fonctions :  
  
 [!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]  
  
 Enfin, le **Assistant contrôle ActiveX** modifie le projet de contrôle. Fichier IDL. Le **concédé sous licence** mot clé est ajouté à la déclaration de la coclasse du contrôle, comme dans l’exemple suivant :  
  
 [!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]  
  
##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a> Personnalisation de la gestion des licences d’un contrôle ActiveX  
 Étant donné que `VerifyUserLicense`, `GetLicenseKey`, et `VerifyLicenseKey` sont déclarés comme fonctions membres virtuelles de la classe de fabrique de contrôle, vous pouvez personnaliser le comportement du contrôle licence.  
  
 Par exemple, vous pouvez fournir plusieurs niveaux de licence pour le contrôle en substituant la `VerifyUserLicense` ou `VerifyLicenseKey` fonctions membres. À l’intérieur de cette fonction, vous pouvez spécifier les propriétés ou les méthodes sont exposées à l’utilisateur en fonction du niveau de licence que vous avez détecté.  
  
 Vous pouvez également ajouter du code pour le `VerifyLicenseKey` fonction qui fournit une méthode personnalisée pour informer l’utilisateur qui contrôlent la création a échoué. Par exemple, dans votre `VerifyLicenseKey` zone de fonction membre que vous pouvez afficher un message indiquant que le contrôle a échoué pour initialiser et pourquoi.  
  
> [!NOTE]
>  Une autre façon de personnaliser la vérification des licences contrôle ActiveX est à la base de données d’inscription pour une clé de Registre spécifiques, au lieu d’appeler `AfxVerifyLicFile`. Pour obtenir un exemple de l’implémentation par défaut, consultez la [les Modifications de fichiers de mise en œuvre](#_core_implementation_file_modifications) section de cet article.  
  
 Pour davantage d’informations sur les problèmes de gestion de licences, consultez les problèmes de gestion de licences dans [mise à niveau d’un contrôle ActiveX](../mfc/upgrading-an-existing-activex-control.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Contrôle ActiveX MFC, Assistant](../mfc/reference/mfc-activex-control-wizard.md)

