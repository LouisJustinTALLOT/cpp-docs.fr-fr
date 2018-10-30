---
title: 'Contrôles ActiveX MFC : Licences des contrôles ActiveX | Microsoft Docs'
ms.custom: ''
ms.date: 09/12/2018
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
ms.openlocfilehash: d7f9c3eeda36c6894103c96f1031f6770daf0c71
ms.sourcegitcommit: a3c9e7888b8f437a170327c4c175733ad9eb0454
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50204715"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>Contrôles ActiveX MFC : gestion des licences d'un contrôle ActiveX

Gestion des licences prise en charge, une fonctionnalité facultative de contrôles ActiveX, vous permet de contrôler qui peut utiliser ou distribuer le contrôle. (Pour plus d’informations sur des problèmes de licence, consultez les problèmes de licence dans [la mise à niveau d’un contrôle ActiveX](../mfc/upgrading-an-existing-activex-control.md).)

>[!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour tout nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

Cet article aborde les rubriques suivantes :

- [Vue d’ensemble de licence des contrôles ActiveX](#_core_overview_of_activex_control_licensing)

- [Création d’un contrôle sous licence](#_core_creating_a_licensed_control)

- [Support de licence](#_core_licensing_support)

- [Personnalisation de la gestion des licences d’un contrôle ActiveX](#_core_customizing_the_licensing_of_an_activex_control)

Contrôles ActiveX qui implémentent des licences vous permettent, en tant que le développeur de contrôle, afin de déterminer la façon dont les autres personnes vont utiliser le contrôle ActiveX. Vous fournissez à l’acheteur avec le contrôle et. LIC avec l’accord que l’acheteur peut distribuer le contrôle, mais pas le. LIC avec une application qui utilise le contrôle. Cela empêche les utilisateurs de l’application à partir de l’écriture de nouvelles applications qui utilisent le contrôle, sans la première licence le contrôle de votre part.

##  <a name="_core_overview_of_activex_control_licensing"></a> Vue d’ensemble de licence des contrôles ActiveX

Pour fournir un support de licence pour les contrôles ActiveX, les [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) classe fournit une implémentation de plusieurs fonctions dans le `IClassFactory2` interface : `IClassFactory2::RequestLicKey`, `IClassFactory2::GetLicInfo`, et `IClassFactory2::CreateInstanceLic`. Lorsque le développeur d’applications conteneur effectue une demande pour créer une instance du contrôle, un appel à `GetLicInfo` est effectué pour vérifier que le contrôle. Fichier de contrat de licence est présent. Si le contrôle est concédé sous licence, une instance du contrôle peut être créée et placée dans le conteneur. Une fois que le développeur a terminé la construction de l’application de conteneur, un autre appel de fonction, cette fois, de `RequestLicKey`, est effectuée. Cette fonction retourne une clé de licence (une simple chaîne de caractères) à l’application de conteneur. La clé retournée est ensuite incorporée à l’application.

La figure ci-dessous illustre la vérification de licence d’un contrôle ActiveX qui sera utilisé pendant le développement d’une application conteneur. Comme mentionné précédemment, le développeur d’applications de conteneur doit avoir la bonne. LIC approprié sur l’ordinateur de développement pour créer une instance du contrôle.

![Contrôle ActiveX vérifié au développement d’une licence](../mfc/media/vc374d1.gif "vc374d1") vérification d’une licence au cours de développement de contrôles ActiveX

Le processus suivant, illustré dans la figure suivante, se produit lorsque l’utilisateur final exécute l’application de conteneur.

Lorsque l’application est démarrée, une instance du contrôle doit généralement être créé. Le conteneur pour cela, en effectuant un appel à `CreateInstanceLic`, en passant de la clé de licence incorporée en tant que paramètre. Une comparaison de chaînes est ensuite effectuée entre la clé de licence incorporée et la copie du contrôle de la clé de licence. Si la correspondance est réussie, une instance du contrôle est créée et l’application continue à s’exécuter normalement. Notez que le. Fichier de contrat de licence ne sont pas nécessairement présent sur l’ordinateur de l’utilisateur contrôle.

![Contrôle ActiveX vérifié lors de l’exécution d’une licence](../mfc/media/vc374d2.gif "vc374d2") vérification d’une licence contrôle ActiveX pendant l’exécution

Licences de contrôle se compose de deux composants de base : un code spécifique dans l’implémentation du contrôle DLL et le fichier de licence. Le code est composé de deux (ou peut-être trois) appels de fonction et une chaîne de caractères, ci-après dénommé « chaîne de licence », contenant une mention de copyright. Ces appels et la chaîne de licence se trouvent dans l’implémentation du contrôle (. Fichier CPP). Le fichier de licence, généré par l’Assistant contrôle ActiveX, est un fichier texte avec une déclaration de copyright. Il est nommé en utilisant le nom de projet avec un. LIC, par exemple SAMPLE. CONTRAT DE LICENCE. Doit être accompagné d’un contrôle sous licence par le fichier de licence si vous avez besoin des utiliser au moment du design.

##  <a name="_core_creating_a_licensed_control"></a> Création d’un contrôle sous licence

Lorsque vous utilisez l’Assistant contrôle ActiveX pour créer l’infrastructure de contrôle, il est facile d’inclure la prise en charge de gestion de licences. Lorsque vous spécifiez que le contrôle doit avoir une licence d’exécution, l’Assistant contrôle ActiveX ajoute du code à la classe de contrôle pour prendre en charge la gestion des licences. Le code se compose de fonctions qui utilisent un fichier de clé et de licence pour la vérification de licence. Ces fonctions peuvent également être modifiées pour personnaliser la licence du contrôle. Pour plus d’informations sur la personnalisation de la licence, consultez [personnalisation de la licence d’un contrôle ActiveX](#_core_customizing_the_licensing_of_an_activex_control) plus loin dans cet article.

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>Pour ajouter la prise en charge pour la gestion des licences avec l’Assistant contrôle ActiveX lorsque vous créez votre projet de contrôle

1. Suivez les instructions de [création d’un contrôle ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md). Le **paramètres d’Application** page de l’Assistant contrôle ActiveX contient l’option pour créer le contrôle avec la licence de l’exécution.

L’Assistant contrôle ActiveX génère maintenant une infrastructure de contrôle ActiveX qui inclut le support de licence de base. Pour obtenir une explication détaillée du code de licence, consultez la rubrique suivante.

##  <a name="_core_licensing_support"></a> Support de licence

Lorsque vous utilisez l’Assistant contrôle ActiveX pour ajouter la prise en charge des licences à un contrôle ActiveX, l’Assistant contrôle ActiveX ajoute le code qui déclare et implémente la fonction de licence est ajouté à l’en-tête de contrôle et de la mise en œuvre les fichiers. Ce code est composé d’un `VerifyUserLicense` fonction membre et un `GetLicenseKey` fonction membre, qui remplacent les implémentations par défaut trouvées dans [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) . Ces fonctions récupérer et vérifier la licence du contrôle.

> [!NOTE]
>  Une troisième fonction membre, `VerifyLicenseKey` n’est pas généré par l’Assistant contrôle ActiveX, mais peut être substituée pour personnaliser le comportement de vérification de la clé de licence.

Ces fonctions membres sont :

- [VerifyUserLicense](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)

   Vérifie que le contrôle autorise l’utilisation au moment du design en vérifiant le système la présence du fichier de licence du contrôle. Cette fonction est appelée par l’infrastructure en tant que partie du traitement `IClassFactory2::GetLicInfo` et `IClassFactory::CreateInstanceLic`.

- [GetLicenseKey](../mfc/reference/coleobjectfactory-class.md#getlicensekey)

   Demande une clé unique à partir de la DLL du contrôle. Cette clé est incorporée dans l’application de conteneur et utilisée plus tard, conjointement avec `VerifyLicenseKey`, pour créer une instance du contrôle. Cette fonction est appelée par l’infrastructure en tant que partie du traitement `IClassFactory2::RequestLicKey`.

- [VerifyLicenseKey](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)

   Vérifie que la clé incorporée et la clé unique du contrôle sont identiques. Ainsi, le conteneur créer une instance du contrôle pour son utilisation. Cette fonction est appelée par l’infrastructure en tant que partie du traitement `IClassFactory2::CreateInstanceLic` et peut être substituée pour assurer une vérification personnalisée de la clé de licence. L’implémentation par défaut effectue une comparaison de chaînes. Pour plus d’informations, consultez [personnalisation de la licence d’un contrôle ActiveX](#_core_customizing_the_licensing_of_an_activex_control), plus loin dans cet article.

###  <a name="_core_header_file_modifications"></a> Modifications de fichier d’en-tête

L’Assistant contrôle ActiveX place le code suivant dans le fichier d’en-tête. Dans cet exemple, deux fonctions membres de `CSampleCtrl`de l’objet `factory` sont déclarées, l’autre qui vérifie la présence du contrôle. Fichier de contrat de licence et une autre qui Récupère la clé de licence à utiliser dans l’application contenant le contrôle :

[!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

###  <a name="_core_implementation_file_modifications"></a> Modifications de fichier d’implémentation

L’Assistant contrôle ActiveX place les deux instructions suivantes dans le fichier d’implémentation pour déclarer le nom de fichier de licence et la chaîne de licence :

[!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
>  Si vous modifiez `szLicString` de quelque façon, vous devez également modifier la première ligne dans le contrôle. Fichier de contrat de licence ou le Gestionnaire de licences ne fonctionnera pas correctement.

L’Assistant contrôle ActiveX place le code suivant dans le fichier d’implémentation pour définir la classe de contrôle `VerifyUserLicense` et `GetLicenseKey` fonctions :

[!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

Enfin, le **Assistant contrôle ActiveX** modifie le projet de contrôle. Fichier IDL. Le **concédé sous licence** mot clé est ajoutée à la déclaration de coclasse du contrôle, comme dans l’exemple suivant :

[!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a> Personnalisation de la gestion des licences d’un contrôle ActiveX

Étant donné que `VerifyUserLicense`, `GetLicenseKey`, et `VerifyLicenseKey` sont déclarés comme fonctions membres virtuelles de la classe de fabrique de contrôle, vous pouvez personnaliser le comportement du contrôle licence.

Par exemple, vous pouvez fournir plusieurs niveaux de licence pour le contrôle en substituant la `VerifyUserLicense` ou `VerifyLicenseKey` fonctions membres. À l’intérieur de cette fonction, vous pouvez ajuster les propriétés ou les méthodes sont exposées à l’utilisateur en fonction du niveau de licence que vous avez détecté.

Vous pouvez également ajouter du code pour le `VerifyLicenseKey` fonction qui fournit une méthode personnalisée pour informer l’utilisateur qui contrôlent la création a échoué. Par exemple, dans votre `VerifyLicenseKey` zone de fonction membre que vous pouvez afficher un message indiquant que le contrôle a échoué pour initialiser et pourquoi.

> [!NOTE]
>  Une autre façon de personnaliser la vérification de licence du contrôle ActiveX consiste à vérifier la base de données d’inscription pour une clé de Registre spécifique, au lieu d’appeler `AfxVerifyLicFile`. Pour obtenir un exemple de l’implémentation par défaut, consultez le [Modifications de fichier d’implémentation](#_core_implementation_file_modifications) section de cet article.

Pour plus d’informations sur des problèmes de licence, consultez les problèmes de licence dans [la mise à niveau d’un contrôle ActiveX](../mfc/upgrading-an-existing-activex-control.md).

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Contrôle ActiveX MFC, Assistant](../mfc/reference/mfc-activex-control-wizard.md)

