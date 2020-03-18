---
title: "Contrôles ActiveX MFC : gestion des licences d'un contrôle ActiveX"
ms.date: 11/19/2018
helpviewer_keywords:
- COleObjectFactory class [MFC], licensing controls
- MFC ActiveX controls [MFC], licensing
- VerifyLicenseKey method [MFC]
- VerifyUserLicense method [MFC]
- GetLicenseKey method [MFC]
- licensing ActiveX controls
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
ms.openlocfilehash: b08abdc0e2c17cb61c0c6a14cd712ec32ea816bd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438023"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>Contrôles ActiveX MFC : gestion des licences d'un contrôle ActiveX

La prise en charge des licences, une fonctionnalité facultative des contrôles ActiveX, vous permet de contrôler qui peut utiliser ou distribuer le contrôle. (Pour plus d’informations sur les problèmes de licences, consultez problèmes de gestion des licences dans la [mise à niveau d’un contrôle ActiveX existant](../mfc/upgrading-an-existing-activex-control.md).)

> [!IMPORTANT]
> ActiveX est une technologie héritée qui ne doit pas être utilisée pour un nouveau développement. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, consultez [contrôles ActiveX](activex-controls.md).

Cet article aborde les thèmes suivants :

- [Vue d’ensemble des licences de contrôles ActiveX](#_core_overview_of_activex_control_licensing)

- [Création d’un contrôle sous licence](#_core_creating_a_licensed_control)

- [Support des licences](#_core_licensing_support)

- [Personnalisation de la gestion des licences d’un contrôle ActiveX](#_core_customizing_the_licensing_of_an_activex_control)

Les contrôles ActiveX qui implémentent les licences vous permettent, en tant que développeur de contrôle, de déterminer comment d’autres personnes utiliseront le contrôle ActiveX. Vous fournissez à l’acheteur de contrôle le contrôle et. Fichier LIC, avec l’accord indiquant que l’acheteur peut distribuer le contrôle, mais pas le. Fichier LIC, avec une application qui utilise le contrôle. Cela empêche les utilisateurs de cette application d’écrire de nouvelles applications qui utilisent le contrôle, sans avoir d’abord la licence du contrôle.

##  <a name="_core_overview_of_activex_control_licensing"></a>Vue d’ensemble des licences de contrôles ActiveX

Pour assurer la prise en charge des licences pour les contrôles ActiveX, la classe [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) fournit une implémentation pour plusieurs fonctions dans l’interface `IClassFactory2` : `IClassFactory2::RequestLicKey`, `IClassFactory2::GetLicInfo`et `IClassFactory2::CreateInstanceLic`. Lorsque le développeur de l’application de conteneur émet une requête pour créer une instance du contrôle, un appel à `GetLicInfo` est effectué pour vérifier le contrôle. Le fichier LIC est présent. Si le contrôle possède une licence, une instance du contrôle peut être créée et placée dans le conteneur. Une fois que le développeur a fini de construire l’application conteneur, un autre appel de fonction, cette fois pour `RequestLicKey`, est effectué. Cette fonction retourne une clé de licence (une chaîne de caractères simple) à l’application conteneur. La clé retournée est ensuite incorporée dans l’application.

La figure ci-dessous illustre la vérification de la licence d’un contrôle ActiveX qui sera utilisé lors du développement d’une application de conteneur. Comme mentionné précédemment, le développeur d’applications de conteneur doit avoir le bon. Fichier LIC installé sur l’ordinateur de développement pour créer une instance du contrôle.

![Contrôle ActiveX sous licence vérifié au développement](../mfc/media/vc374d1.gif "Contrôle ActiveX sous licence vérifié au développement") <br/>
Vérification d’un contrôle ActiveX sous licence pendant le développement

Le processus suivant, illustré dans la figure suivante, se produit lorsque l’utilisateur final exécute l’application conteneur.

Lorsque l’application est démarrée, une instance du contrôle doit généralement être créée. Pour ce faire, le conteneur effectue un appel à `CreateInstanceLic`, en transmettant la clé de licence incorporée en tant que paramètre. Une comparaison de chaînes est ensuite établie entre la clé de licence incorporée et la propre copie du contrôle de la clé de licence. Si la correspondance est réussie, une instance du contrôle est créée et l’application continue de s’exécuter normalement. Notez que le. Le fichier LIC n’a pas besoin d’être présent sur l’ordinateur de l’utilisateur du contrôle.

![Contrôle ActiveX sous licence vérifié au moment de l’exécution](../mfc/media/vc374d2.gif "Contrôle ActiveX sous licence vérifié au moment de l'exécution") <br/>
Vérification d’un contrôle ActiveX sous licence au cours de l’exécution

La gestion des licences est constituée de deux composants de base : un code spécifique dans la DLL d’implémentation de contrôle et le fichier de licence. Le code est composé de deux (voire trois) appels de fonction et d’une chaîne de caractères, ci-après, appelée « chaîne de licence », contenant une mention de droits d’auteur. Ces appels et la chaîne de licence se trouvent dans l’implémentation du contrôle (. CPP). Le fichier de licence, généré par l’Assistant contrôle ActiveX, est un fichier texte avec une déclaration de copyright. Elle est nommée en utilisant le nom du projet avec un. Extension LIC, par exemple. Profil. Un contrôle sous licence doit être accompagné du fichier de licence si une utilisation au moment de la conception est nécessaire.

##  <a name="_core_creating_a_licensed_control"></a>Création d’un contrôle sous licence

Lorsque vous utilisez l’Assistant contrôle ActiveX pour créer l’infrastructure de contrôle, il est facile d’inclure la prise en charge des licences. Lorsque vous spécifiez que le contrôle doit avoir une licence d’exécution, l’Assistant contrôle ActiveX ajoute du code à la classe de contrôle pour prendre en charge la gestion des licences. Le code se compose de fonctions qui utilisent un fichier de clé et de licence pour la vérification de licence. Ces fonctions peuvent également être modifiées pour personnaliser le contrôle de licence. Pour plus d’informations sur la personnalisation des licences, consultez [Personnalisation de la gestion des licences d’un contrôle ActiveX](#_core_customizing_the_licensing_of_an_activex_control) plus loin dans cet article.

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>Pour ajouter la prise en charge de la gestion des licences avec l’Assistant contrôle ActiveX lors de la création de votre projet de contrôle

1. Utilisez les instructions de [création d’un contrôle ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md). La page Paramètres de l' **application** de l’Assistant contrôle ActiveX contient l’option permettant de créer le contrôle avec la licence d’exécution.

L’Assistant contrôle ActiveX génère à présent une infrastructure de contrôle ActiveX qui comprend la prise en charge des licences de base. Pour obtenir une explication détaillée du code de licence, consultez la rubrique suivante.

##  <a name="_core_licensing_support"></a>Support des licences

Lorsque vous utilisez l’Assistant contrôle ActiveX pour ajouter la prise en charge des licences à un contrôle ActiveX, l’Assistant contrôle ActiveX ajoute du code qui déclare et implémente la fonctionnalité de gestion des licences est ajoutée aux fichiers d’en-tête et d’implémentation du contrôle. Ce code est composé d’une fonction membre `VerifyUserLicense` et d’une fonction membre `GetLicenseKey`, qui remplacent les implémentations par défaut trouvées dans [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) . Ces fonctions récupèrent et vérifient la licence de contrôle.

> [!NOTE]
>  Une troisième fonction membre, `VerifyLicenseKey` n’est pas générée par l’Assistant contrôle ActiveX, mais peut être substituée pour personnaliser le comportement de vérification de la clé de licence.

Ces fonctions membres sont les suivantes :

- [VerifyUserLicense](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)

   Vérifie que le contrôle autorise l’utilisation au moment du design en vérifiant la présence du fichier de licence de contrôle dans le système. Cette fonction est appelée par l’infrastructure dans le cadre du traitement des `IClassFactory2::GetLicInfo` et des `IClassFactory::CreateInstanceLic`.

- [GetLicenseKey](../mfc/reference/coleobjectfactory-class.md#getlicensekey)

   Demande une clé unique à partir de la DLL de contrôle. Cette clé est incorporée dans l’application conteneur et utilisée ultérieurement, conjointement avec `VerifyLicenseKey`, pour créer une instance du contrôle. Cette fonction est appelée par l’infrastructure dans le cadre du traitement des `IClassFactory2::RequestLicKey`.

- [VerifyLicenseKey](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)

   Vérifie que la clé incorporée et la clé unique du contrôle sont identiques. Cela permet au conteneur de créer une instance du contrôle pour son utilisation. Cette fonction est appelée par l’infrastructure dans le cadre du traitement `IClassFactory2::CreateInstanceLic` et peut être substituée pour fournir une vérification personnalisée de la clé de licence. L’implémentation par défaut effectue une comparaison de chaînes. Pour plus d’informations, consultez [Personnalisation de la gestion des licences d’un contrôle ActiveX](#_core_customizing_the_licensing_of_an_activex_control), plus loin dans cet article.

###  <a name="_core_header_file_modifications"></a>Modifications du fichier d’en-tête

L’Assistant contrôle ActiveX place le code suivant dans le fichier d’en-tête du contrôle. Dans cet exemple, deux fonctions membres de l’objet `CSampleCtrl``factory` sont déclarées, une qui vérifie la présence du contrôle. Fichier LIC et un autre qui récupère la clé de licence à utiliser dans l’application contenant le contrôle :

[!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

###  <a name="_core_implementation_file_modifications"></a>Modifications du fichier d’implémentation

L’Assistant contrôle ActiveX place les deux instructions suivantes dans le fichier d’implémentation de contrôle pour déclarer le nom de fichier de licence et la chaîne de licence :

[!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
>  Si vous modifiez `szLicString` de quelque façon que ce soit, vous devez également modifier la première ligne dans le contrôle. Le fichier LIC ou les licences ne fonctionneront pas correctement.

L’Assistant contrôle ActiveX place le code suivant dans le fichier d’implémentation du contrôle pour définir les fonctions `VerifyUserLicense` et `GetLicenseKey` de la classe de contrôle :

[!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

Enfin, l' **Assistant contrôle ActiveX** modifie le projet de contrôle. Fichier IDL. Le mot clé **sous licence** est ajouté à la déclaration de coclasse du contrôle, comme dans l’exemple suivant :

[!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a>Personnalisation de la gestion des licences d’un contrôle ActiveX

Étant donné que `VerifyUserLicense`, `GetLicenseKey`et `VerifyLicenseKey` sont déclarés comme fonctions membres virtuelles de la classe de fabrique de contrôle, vous pouvez personnaliser le comportement de licence du contrôle.

Par exemple, vous pouvez fournir plusieurs niveaux de licence pour le contrôle en substituant les fonctions membres `VerifyUserLicense` ou `VerifyLicenseKey`. À l’intérieur de cette fonction, vous pouvez ajuster les propriétés ou méthodes exposées à l’utilisateur en fonction du niveau de licence que vous avez détecté.

Vous pouvez également ajouter du code à la fonction `VerifyLicenseKey` qui fournit une méthode personnalisée pour informer l’utilisateur que la création du contrôle a échoué. Par exemple, dans votre fonction membre `VerifyLicenseKey`, vous pouvez afficher une boîte de message indiquant que l’initialisation du contrôle a échoué et pourquoi.

> [!NOTE]
>  Une autre façon de personnaliser la vérification des licences de contrôle ActiveX consiste à vérifier la base de données d’inscription pour obtenir une clé de Registre spécifique, au lieu d’appeler `AfxVerifyLicFile`. Pour obtenir un exemple de l’implémentation par défaut, consultez la section [mise en œuvre des modifications de fichiers](#_core_implementation_file_modifications) dans cet article.

Pour plus d’informations sur les problèmes de licences, consultez problèmes de gestion des licences dans la [mise à niveau d’un contrôle ActiveX existant](../mfc/upgrading-an-existing-activex-control.md).

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Contrôle ActiveX MFC, Assistant](../mfc/reference/mfc-activex-control-wizard.md)
