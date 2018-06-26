---
title: Contrôles ActiveX sur Internet | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [MFC], creating
- ActiveX controls [MFC], Internet
- downloading data with ActiveX controls
- OLE controls [MFC], upgrading to ActiveX
- Internet applications [MFC], ActiveX controls
- networks [MFC], downloading with ActiveX controls
ms.assetid: 7ab943c8-2022-41df-9065-d629b616eeec
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 02a4c2e8d9da553ffe14c8d9d061d11d7357c19c
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931975"
---
# <a name="activex-controls-on-the-internet"></a>Contrôles ActiveX sur Internet
Les contrôles ActiveX sont la version mise à jour de la spécification de contrôle OLE. Les contrôles sont une architecture primaire pour le développement de composants logiciels programmables qui peuvent être utilisés dans plusieurs conteneurs, y compris les navigateurs Web compatibles COM sur Internet. Un contrôle ActiveX peut être un contrôle Internet et peut ajouter ses fonctionnalités dans un document actif ou faire partie d'une page Web. Les contrôles sur une page web peuvent communiquer entre eux à l’aide de scripts.  
  
 Les contrôles ActiveX ne sont pas limités à Internet. Un contrôle ActiveX peut également être utilisé dans n'importe quel conteneur, tant que le contrôle prend en charge les interfaces requises par ce conteneur.  
  
 **Contrôles ActiveX ont plusieurs avantages, notamment :**  
  
-   Moins d'interfaces requises que les contrôles OLE précédents.  
  
-   La possibilité d'être sans fenêtre et toujours actifs en place.  
  
 **Pour être un contrôle ActiveX, un contrôle doit :**  
  
-   Prise en charge la `IUnknown` interface.  
  
-   Être un objet COM.  
  
-   Exporter **DLLRegisterServer** et **DLLUnRegisterServer**.  
  
-   Prendre en charge des interfaces supplémentaires si nécessaires pour la fonctionnalité.  
  
## <a name="making-your-existing-controls-internet-friendly"></a>Adaptation de vos contrôles existants à Internet  
 Concevoir un contrôle qui fonctionne bien dans un environnement Internet nécessite de faire attention aux débits de transmission relativement faibles sur Internet. Vous pouvez utiliser les contrôles existants ; toutefois, vous devez effectuer certaines étapes pour réduire le nombre d'instructions et effectuer le téléchargement des propriétés de votre contrôle de manière asynchrone.  
  
 Pour améliorer les performances de vos contrôles, suivez ces recommandations en matière d'efficacité :  
  
-   Implémentez les techniques décrites dans l’article [contrôles ActiveX : optimisation](../mfc/mfc-activex-controls-optimization.md).  
  
-   Déterminez comment un contrôle est instancié.  
  
-   Soyez asynchrone ; ne retardez pas d'autres programmes.  
  
-   Téléchargez les données par petits blocs.  
  
     En téléchargeant des flux volumineux, tels que des fichiers bitmap ou des données vidéo, accédez aux données d'un contrôle en coopération avec le conteneur. Récupérez des données de façon incrémentielle ou progressive, en travaillant en coopération avec d'autres contrôles qui peuvent aussi récupérer des données. Ce code peut également être téléchargé de manière asynchrone.  
  
-   Téléchargez le code et les propriétés en arrière-plan.  
  
-   Soyez aussi actif que possible au niveau de l'interface utilisateur.  
  
-   Considérez la manière dont les données permanentes sont enregistrées, à la fois pour les propriétés et les importantes données BLOB (par exemple une image bitmap ou des données vidéo).  
  
     Les contrôles avec des quantités importantes de données permanentes, telles que des fichiers bitmap ou AVI, requièrent une attention particulière à la méthode de téléchargement. Un document ou une page peut être visible dès que possible, et permet à l'utilisateur d'interagir avec la page lorsque les contrôles extraient des données en arrière-plan.  
  
-   Entrez des routines efficaces pour réduire le nombre et l'exécution d'instructions.  
  
     Les contrôles d'étiquette et de petits boutons, avec seulement quelques octets de données persistantes, conviennent pour une utilisation dans l'environnement Internet et fonctionnent correctement à l'intérieur des navigateurs.  
  
-   Considérez que la progression est communiquée au conteneur.  
  
     Informez le conteneur de la progression du téléchargement asynchrone, notamment lorsque l'utilisateur peut commencer à interagir avec une page, et si le téléchargement est terminé. Le conteneur peut afficher la progression à l'utilisateur, tels que les pourcentages atteints.  
  
-   Déterminez comment les contrôles sont stockés sur l'ordinateur client.  
  
## <a name="creating-a-new-activex-control"></a>Création d'un contrôle ActiveX  
 Lors de la création d'un contrôle avec l'Assistant Application, vous pouvez choisir d'activer la prise en charge des monikers asynchrones ainsi que des optimisations supplémentaires. Pour ajouter la prise en charge des propriétés de téléchargement asynchrone, procédez comme suit :  
  
#### <a name="to-create-your-project-using-the-mfc-activex-control-wizard"></a>Pour créer votre projet à l'aide de l'Assistant Contrôle ActiveX MFC  
  
1.  Cliquez sur **nouveau** sur la **fichier** menu.  
  
2.  Sélectionnez **Assistant contrôle ActiveX MFC** à partir de Visual C++, projets et nommez votre projet.  
  
3.  Sur le **paramètres de contrôle** page, sélectionnez **charge les propriétés de façon asynchrone**. Cette option configure la propriété d'état Prêt et l'événement de modification d'état prêt pour vous.  
  
     Vous pouvez également sélectionner des optimisations supplémentaires, telles que **l’activation sans fenêtre**, qui est décrite dans [contrôles ActiveX : optimisation](../mfc/mfc-activex-controls-optimization.md).  
  
4.  Choisissez **Terminer** pour créer le projet.  
  
#### <a name="to-create-a-class-derived-from-cdatapathproperty"></a>Pour créer une classe dérivée de CDataPathProperty  
  
1.  Créez une classe dérivée de `CDataPathProperty`.  
  
2.  Dans chacun de vos fichiers sources qui contiennent le fichier d'en-tête pour le contrôle, ajoutez le fichier d'en-tête pour cette classe avant celui-ci.  
  
3.  Dans cette classe, remplacez `OnDataAvailable`. Cette fonction est appelée lorsque les données sont disponibles pour l'affichage. Lorsque des données deviennent disponibles, vous pouvez les gérer avec la méthode de votre choix, par exemple avec un affichage progressif.  
  
     L'extrait de code ci-dessous est un exemple simple d'affichage progressif des données dans un contrôle d'édition. Notez l’utilisation de l’indicateur **BSCF_FIRSTDATANOTIFICATION** pour effacer le contrôle d’édition.  
  
     [!code-cpp[NVC_MFCActiveXControl#1](../mfc/codesnippet/cpp/activex-controls-on-the-internet_1.cpp)]  
  
     Notez que vous devez inclure AFXCMN.H pour utiliser la classe `CListCtrl`.  
  
4.  Lorsque votre contrôle change d'état général (par exemple, de "en chargement" à "initialisé" ou "en interaction utilisateur"), appelez `COleControl::InternalSetReadyState`. Si le contrôle a une propriété de chemin d’accès de données qu’une seule, vous pouvez ajouter du code sur **BSCF_LASTDATANOTIFICATION** pour notifier au conteneur que le téléchargement est terminé. Exemple :  
  
     [!code-cpp[NVC_MFCActiveXControl#2](../mfc/codesnippet/cpp/activex-controls-on-the-internet_2.cpp)]  
  
5.  Substituez `OnProgress` Dans `OnProgress`, il vous est renvoyé un nombre qui indique la plage maximale et un nombre indiquant l'avancement du téléchargement en cours. Vous pouvez utiliser ces nombres pour afficher l'état, comme le pourcentage de progression.  
  
 La procédure suivante ajoute une propriété au contrôle pour utiliser uniquement la classe qui vient d'être dérivée.  
  
#### <a name="to-add-a-property"></a>Pour ajouter une propriété  
  
1.  Dans **affichage de classes**, avec le bouton droit de l’interface sous le nœud de bibliothèque et sélectionnez **ajouter**, puis **ajouter une propriété**. Ceci démarrera le **Assistant Ajout de propriété**.  
  
2.  Dans le **Assistant Ajout de propriété**, sélectionnez le **méthodes Set/Get** case d’option, tapez le **nom de la propriété**, par exemple, EditControlText et sélectionnez BSTR comme le **Type de propriété**.  
  
3.  Cliquez sur **Terminer**.  
  
4.  Déclarez une variable membre de votre classe dérivée de `CDataPathProperty` à votre classe de contrôle ActiveX.  
  
     [!code-cpp[NVC_MFCActiveXControl#3](../mfc/codesnippet/cpp/activex-controls-on-the-internet_3.h)]  
  
5.  Implémentez les méthodes `Get/Set`. Pour `Get`, la chaîne de retour. Pour `Set`, chargez la propriété et appelez `SetModifiedFlag`.  
  
     [!code-cpp[NVC_MFCActiveXControl#4](../mfc/codesnippet/cpp/activex-controls-on-the-internet_4.cpp)]  
  
6.  Dans [DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange), ajoutez la ligne suivante :  
  
     [!code-cpp[NVC_MFCActiveXControl#5](../mfc/codesnippet/cpp/activex-controls-on-the-internet_5.cpp)]  
  
7.  Substituer [ResetData](../mfc/reference/cdatapathproperty-class.md#resetdata) pour notifier la propriété à réinitialiser son contrôle en ajoutant cette ligne :  
  
     [!code-cpp[NVC_MFCActiveXControl#6](../mfc/codesnippet/cpp/activex-controls-on-the-internet_6.cpp)]  
  
## <a name="deciding-whether-to-derive-from-cdatapathproperty-or-ccacheddatapathproperty"></a>Choisir d'effectuer une dérivation à partir de CDataPathProperty ou de CCachedDataPathProperty  
 L'exemple précédent décrit les étapes pour dériver la propriété de votre contrôle à partir de `CDataPathProperty`. Il s'agit d'un bon choix si vous téléchargez des données en temps réel qui changent fréquemment, et pour lesquelles vous n'avez pas besoin de conserver toutes les données, mais uniquement la valeur actuelle. Par exemple, le contrôle de cotations boursières.  
  
 Vous pouvez également effectuer une dérivation à partir de `CCachedDataPathProperty`. Dans ce cas, les données téléchargées sont mises en cache dans un fichier de stockage. Il s'agit d'un bon choix si vous devez conserver toutes les données téléchargées (par exemple, un contrôle qui affiche progressivement une image bitmap). Dans ce cas, la classe possède une variable membre contenant les données :  
  
 `CMemFile m_Cache;`  
  
 Dans votre classe de contrôle ActiveX, vous pouvez utiliser ce fichier mappé en mémoire dans `OnDraw` pour afficher les données. Dans votre classe de contrôle ActiveX dérivée `CCachedDataPathProperty`, substituez la fonction membre `OnDataAvailable` et invalidez le contrôle, après avoir appelé l'implémentation de la classe de base.  
  
 [!code-cpp[NVC_MFCActiveXControl#7](../mfc/codesnippet/cpp/activex-controls-on-the-internet_7.cpp)]  
  
## <a name="downloading-data-asynchronously-using-activex-controls"></a>Téléchargement de données en mode asynchrone à l'aide des contrôles ActiveX  
 Le téléchargement de données sur un réseau doit être effectué de manière asynchrone. L'avantage de cette opération est que si un grand nombre de données est transféré ou si la connexion est lente, l'opération de téléchargement ne bloquera pas d'autres processus exécutés sur le client.  
  
 Des monikers asynchrones permettent de télécharger les données sur un réseau en mode asynchrone. Une opération de lecture dans un moniker asynchrone retourne immédiatement le résultat, même si l'opération n'a pas été effectuée.  
  
 Par exemple, si seuls dix (10) octets sont disponibles et que la lecture est appelée de manière asynchrone dans un fichier de un (1) Ko, la lecture ne se bloquera pas, mais retournera les dix (10) octets disponibles.  
  
 Vous implémentez [monikers asynchrones](../mfc/asynchronous-monikers-on-the-internet.md) à l’aide de la `CAsyncMonikerFile` classe. Toutefois, les contrôles ActiveX peuvent utiliser la classe `CDataPathProperty`, dérivée de `CAsyncMonikerFile`, pour implémenter des propriétés de contrôle asynchrones.  
  
 L'exemple ASYNDOWN montre comment configurer une boucle asynchrone en utilisant des minuteries pour lire les données. ASYNDOWN est décrit en détail dans l'article de la Base de connaissances relatif à la "procédure : AsyncDown illustre le téléchargement asynchrone de données" (Q177244) et peut être téléchargé à partir du Centre de téléchargement Microsoft. (Pour plus d'informations sur le téléchargement de fichiers à partir du Centre de téléchargement Microsoft, consultez l'article relatif à la "procédure d'obtention des fichiers de support technique Microsoft depuis les services en ligne" (Q119591) dans la Base de connaissances Microsoft.) Vous pouvez trouver des articles de la Base de connaissances à [ http://support.microsoft.com/support ](http://support.microsoft.com/support).  
  
 La technique de base utilisée dans ASYNDOWN consiste à définir une minuterie dans **CDataPathProperty::OnDataAvailable** pour indiquer lorsque les données sont disponibles. Si le message de la minuterie est accepté, l'application lit des blocs de 128 octets de données et remplit un contrôle d'édition. Si les données ne sont pas disponibles lorsque le message de la minuterie est traité, la minuterie est désactivée. `OnDataAvailable` démarre la minuterie si davantage de données arrivent ultérieurement.  
  
## <a name="displaying-a-control-on-a-web-page"></a>Affichage d’un contrôle sur une page web  
 Voici un exemple de balise et d’attributs d’objet pour insérer un contrôle sur une page web.  
  
 `<OBJECT`  
  
 `CLASSID="clsid:FC25B780-75BE-11CF-8B01-444553540000"`  
  
 `CODEBASE="/ie/download/activex/iechart.ocx"`  
  
 `ID=chart1`  
  
 `WIDTH=400`  
  
 `HEIGHT=200`  
  
 `ALIGN=center`  
  
 `HSPACE=0`  
  
 `VSPACE=0`  
  
 `>`  
  
 `<PARAM NAME="BackColor" value="#ffffff">`  
  
 `<PARAM NAME="ForeColor" value="#0000ff">`  
  
 `<PARAM NAME="url" VALUE="/ie/controls/chart/mychart.txt">`  
  
 `</OBJECT>`  
  
## <a name="updating-an-existing-ole-control-to-use-new-activex-control-features"></a>Mise à jour d’un contrôle OLE existant pour utiliser les nouvelles fonctionnalités de contrôle ActiveX  
 Si votre contrôle OLE a été créé avec une version de Visual C++ antérieure à la version 4.2, vous pouvez suivre certaines étapes pour améliorer ses performances et ses fonctionnalités. Pour obtenir une présentation détaillée de ces modifications, consultez [contrôles ActiveX : optimisation](../mfc/mfc-activex-controls-optimization.md).  
  
 Si vous ajoutez la prise en charge des propriétés asynchrones à un contrôle existant, vous devrez ajouter la propriété d'état Prêt et l'événement `ReadyStateChange` vous-même. Dans le constructeur de votre contrôle, ajoutez :  
  
 [!code-cpp[NVC_MFCActiveXControl#8](../mfc/codesnippet/cpp/activex-controls-on-the-internet_8.cpp)]  
  
 Vous mettrez à jour l’état prêt lorsque votre code est téléchargé en appelant [COleControl::InternalSetReadyState](../mfc/reference/colecontrol-class.md#internalsetreadystate). Un emplacement à partir duquel vous pouvez appeler `InternalSetReadyState` est depuis la substitution `OnProgress` de la classe dérivée de `CDataPathProperty`.  
  

  
## <a name="see-also"></a>Voir aussi  
 [Tâches de programmation Internet MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Notions de base de la programmation Internet MFC](../mfc/mfc-internet-programming-basics.md)

