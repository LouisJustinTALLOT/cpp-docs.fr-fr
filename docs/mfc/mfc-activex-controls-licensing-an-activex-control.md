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
ms.openlocfilehash: aaab4ae3bb13790784a66d53b41dbc3a7cdaec89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364607"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>Contrôles ActiveX MFC : gestion des licences d'un contrôle ActiveX

Le support de licence, une fonctionnalité facultative des contrôles ActiveX, vous permet de contrôler qui est capable d’utiliser ou de distribuer le contrôle. (Pour une discussion plus approfondie sur les questions de licence, voir les questions de licence dans [la mise à niveau d’un contrôle actif existant](../mfc/upgrading-an-existing-activex-control.md).)

> [!IMPORTANT]
> ActiveX est une technologie héritée qui ne devrait pas être utilisée pour de nouveaux développements. Pour plus d’informations sur les technologies modernes qui remplacent ActiveX, voir [ActiveX Controls](activex-controls.md).

Cet article aborde les thèmes suivants :

- [Aperçu des licences de contrôle ActiveX](#_core_overview_of_activex_control_licensing)

- [Création d’un contrôle sous licence](#_core_creating_a_licensed_control)

- [Soutien aux licences](#_core_licensing_support)

- [Personnaliser l’octroi de licences d’un contrôle ActiveX](#_core_customizing_the_licensing_of_an_activex_control)

Les contrôles ActiveX qui mettent en œuvre les licences vous permettent, en tant que développeur de contrôle, de déterminer comment d’autres personnes utiliseront le contrôle ActiveX. Vous fournissez à l’acheteur de contrôle le contrôle et . Fichier LIC, avec l’accord que l’acheteur peut distribuer le contrôle, mais pas le . Fichier LIC, avec une application qui utilise le contrôle. Cela empêche les utilisateurs de cette application d’écrire de nouvelles applications qui utilisent le contrôle, sans d’abord autoriser le contrôle de vous.

## <a name="overview-of-activex-control-licensing"></a><a name="_core_overview_of_activex_control_licensing"></a>Aperçu des licences de contrôle ActiveX

Pour fournir un support de licence pour les contrôles ActiveX, la classe [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) fournit une implémentation pour plusieurs fonctions de `IClassFactory2` l’interface: `IClassFactory2::RequestLicKey`, `IClassFactory2::GetLicInfo`, et `IClassFactory2::CreateInstanceLic`. Lorsque le développeur d’applications de conteneurs fait une `GetLicInfo` demande de création d’une instance du contrôle, un appel est fait pour vérifier que le contrôle . Le fichier LIC est présent. Si le contrôle est autorisé, une instance du contrôle peut être créée et placée dans le conteneur. Une fois que le développeur a fini de construire `RequestLicKey`l’application de conteneur, un autre appel de fonction, cette fois à , est faite. Cette fonction renvoie une clé de licence (une simple chaîne de caractères) à l’application de conteneur. La clé retournée est ensuite intégrée dans l’application.

Le chiffre ci-dessous démontre la vérification de licence d’un contrôle ActiveX qui sera utilisé lors de l’élaboration d’une application de conteneurs. Comme mentionné précédemment, le développeur d’applications de conteneurs doit avoir le bon . Fichier LIC installé sur la machine de développement pour créer une instance du contrôle.

![Contrôle ActiveX sous licence vérifié au développement](../mfc/media/vc374d1.gif "Contrôle ActiveX sous licence vérifié au développement") <br/>
Vérification d’un contrôle ActiveX sous licence pendant le développement

Le processus suivant, indiqué dans la figure suivante, se produit lorsque l’utilisateur final exécute l’application du conteneur.

Lorsque l’application est lancée, une instance du contrôle doit généralement être créée. Le conteneur accomplit cela en `CreateInstanceLic`faisant un appel à , en passant la clé de licence intégrée comme un paramètre. Une comparaison de chaîne est ensuite effectuée entre la clé de licence intégrée et la propre copie du contrôle de la clé de licence. Si le match est réussi, une instance du contrôle est créée et l’application continue à s’exécuter normalement. Notez que le . Fichier LIC n’a pas besoin d’être présent sur la machine de l’utilisateur de contrôle.

![Contrôle ActiveX sous licence vérifié au moment de l'exécution](../mfc/media/vc374d2.gif "Contrôle ActiveX sous licence vérifié au moment de l'exécution") <br/>
Vérification d’un contrôle ActiveX sous licence pendant l’exécution

La licence de contrôle se compose de deux composantes de base : le code spécifique dans la mise en œuvre de contrôle DLL et le fichier de licence. Le code est composé de deux (ou peut-être trois) appels de fonction et d’une chaîne de caractères, par la suite appelée « chaîne de licence », contenant un avis de copyright. Ces appels et la chaîne de licence se trouvent dans la mise en œuvre de contrôle (. dossier du RPC. Le fichier de licence, généré par l’Assistant de Contrôle ActiveX, est un fichier texte avec une déclaration de copyright. Il est nommé en utilisant le nom du projet avec un . Extension LIC, par exemple SAMPLE. Lic. Un contrôle autorisé doit être accompagné du fichier de licence si l’utilisation du temps de conception est nécessaire.

## <a name="creating-a-licensed-control"></a><a name="_core_creating_a_licensed_control"></a>Création d’un contrôle sous licence

Lorsque vous utilisez l’Assistant de Contrôle ActiveX pour créer le cadre de contrôle, il est facile d’inclure le support de licence. Lorsque vous spécifiez que le contrôle doit avoir une licence de temps d’exécution, l’Assistant de Contrôle ActiveX ajoute du code à la classe de contrôle pour prendre en charge les licences. Le code se compose de fonctions qui utilisent une clé et un fichier de licence pour la vérification de la licence. Ces fonctions peuvent également être modifiées pour personnaliser la licence de contrôle. Pour plus d’informations sur la personnalisation des licences, voir [Personnaliser la licence d’un contrôle ActiveX](#_core_customizing_the_licensing_of_an_activex_control) plus tard dans cet article.

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>Pour ajouter un support pour la licence avec l’Assistant de Contrôle ActiveX lorsque vous créez votre projet de contrôle

1. Utilisez les instructions pour [créer un contrôle MFC ActiveX](../mfc/reference/creating-an-mfc-activex-control.md). La page **Paramètres d’application** de l’Assistant de Contrôle ActiveX contient l’option de créer le contrôle avec la licence de temps d’exécution.

L’Assistant de Contrôle ActiveX génère maintenant un cadre de contrôle ActiveX qui comprend un support de licence de base. Pour une explication détaillée du code de licence, voir le sujet suivant.

## <a name="licensing-support"></a><a name="_core_licensing_support"></a>Soutien aux licences

Lorsque vous utilisez l’Assistant de Contrôle ActiveX pour ajouter un support de licence à un contrôle ActiveX, l’Assistant de Contrôle ActiveX ajoute du code qui déclare et implémente la capacité de licence est ajouté aux fichiers d’en-tête et de implémentation de contrôle. Ce code est `VerifyUserLicense` composé d’une fonction membre et d’une `GetLicenseKey` fonction membre, qui remplacent les implémentations par défaut trouvées dans [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) . Ces fonctions récupèrent et vérifient la licence de contrôle.

> [!NOTE]
> Une troisième fonction `VerifyLicenseKey` de membre, n’est pas générée par l’Assistant de Contrôle ActiveX, mais peut être remplacée pour personnaliser le comportement de vérification des clés de licence.

Ces fonctions de membre sont les :

- [VerifyUserLicense](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)

   Vérifie que le contrôle permet l’utilisation du temps de conception en vérifiant le système pour la présence du fichier de licence de contrôle. Cette fonction est appelée par le `IClassFactory2::GetLicInfo` `IClassFactory::CreateInstanceLic`cadre dans le cadre du traitement et .

- [GetLicenseKey (en anglais seulement)](../mfc/reference/coleobjectfactory-class.md#getlicensekey)

   Demande une clé unique de la DLL de contrôle. Cette clé est intégrée dans l’application de `VerifyLicenseKey`conteneur et utilisée plus tard, en conjonction avec, pour créer une instance du contrôle. Cette fonction est appelée par le `IClassFactory2::RequestLicKey`cadre dans le cadre du traitement .

- [VerifyLicenseKey (en anglais seulement)](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)

   Vérifie que la clé intégrée et la clé unique du contrôle sont les mêmes. Cela permet au conteneur de créer une instance du contrôle pour son utilisation. Cette fonction est appelée par le `IClassFactory2::CreateInstanceLic` cadre dans le cadre du traitement et peut être remplacée pour fournir une vérification personnalisée de la clé de licence. L’implémentation par défaut effectue une comparaison de chaînes. Pour plus d’informations, voir [Personnaliser la licence d’un contrôle ActiveX](#_core_customizing_the_licensing_of_an_activex_control), plus tard dans cet article.

### <a name="header-file-modifications"></a><a name="_core_header_file_modifications"></a>Modifications de fichiers d’en-tête

L’Assistant de Contrôle ActiveX place le code suivant dans le fichier d’en-tête de contrôle. Dans cet exemple, deux `CSampleCtrl`fonctions `factory` de membre de l’objet sont déclarées, une qui vérifie la présence du contrôle . Fichier LIC et un autre qui récupère la clé de licence à utiliser dans l’application contenant le contrôle:

[!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

### <a name="implementation-file-modifications"></a><a name="_core_implementation_file_modifications"></a>Modifications de fichiers de mise en œuvre

L’Assistant de Contrôle ActiveX place les deux énoncés suivants dans le fichier de mise en œuvre de contrôle pour déclarer le nom de fichier de licence et la chaîne de licence :

[!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
> Si vous `szLicString` modifiez de quelque manière que ce soit, vous devez également modifier la première ligne dans le contrôle . Le fichier ou l’autorisation de LIC ne fonctionnera pas correctement.

L’Assistant de Contrôle ActiveX place le code suivant dans `VerifyUserLicense` `GetLicenseKey` le fichier d’implémentation de contrôle pour définir la classe de contrôle et les fonctions :

[!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

Enfin, **l’Assistant de Contrôle ActiveX** modifie le projet de contrôle. Fichier IDL. Le mot clé **sous licence** est ajouté à la déclaration de coclassation du contrôle, comme dans l’exemple suivant :

[!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

## <a name="customizing-the-licensing-of-an-activex-control"></a><a name="_core_customizing_the_licensing_of_an_activex_control"></a>Personnaliser l’octroi de licences d’un contrôle ActiveX

Parce `VerifyUserLicense` `GetLicenseKey`que `VerifyLicenseKey` , et sont déclarés comme fonctions de membre virtuel de la classe d’usine de contrôle, vous pouvez personnaliser le comportement de licence du contrôle.

Par exemple, vous pouvez fournir plusieurs niveaux de licence `VerifyUserLicense` `VerifyLicenseKey` pour le contrôle en dépassant les fonctions ou les fonctions des membres. A l’intérieur de cette fonction, vous pouvez ajuster les propriétés ou les méthodes exposées à l’utilisateur en fonction du niveau de licence que vous avez détecté.

Vous pouvez également ajouter `VerifyLicenseKey` du code à la fonction qui fournit une méthode personnalisée pour informer l’utilisateur que la création de contrôle a échoué. Par exemple, `VerifyLicenseKey` dans votre fonction de membre, vous pouvez afficher une boîte de message indiquant que le contrôle n’a pas été parastérisé et pourquoi.

> [!NOTE]
> Une autre façon de personnaliser la vérification de licence de contrôle ActiveX `AfxVerifyLicFile`est de vérifier la base de données d’enregistrement pour une clé de registre spécifique, au lieu d’appeler . Pour un exemple de la mise en œuvre par défaut, consultez la section Modifications de fichiers de [mise en œuvre](#_core_implementation_file_modifications) de cet article.

Pour une discussion plus approfondie des questions de licence, voir les questions de licence dans [la mise à niveau d’un contrôle actif existant .](../mfc/upgrading-an-existing-activex-control.md)

## <a name="see-also"></a>Voir aussi

[Contrôles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX Control Wizard](../mfc/reference/mfc-activex-control-wizard.md)
