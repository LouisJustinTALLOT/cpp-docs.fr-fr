---
title: "TN058 : implémentation de l'état du module MFC"
ms.date: 06/28/2018
helpviewer_keywords:
- thread state [MFC]
- module states [MFC], managing state data
- TN058
- MFC, managing state data
- module states [MFC], switching
- DLLs [MFC], module states
- process state [MFC]
ms.assetid: 72f5b36f-b3da-4009-a144-24258dcd2b2f
ms.openlocfilehash: b64fb6b97474007c44a2124315e83e1ac119f9ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366609"
---
# <a name="tn058-mfc-module-state-implementation"></a>TN058 : implémentation de l'état du module MFC

> [!NOTE]
> La note technique suivante n'a pas été mise à jour depuis son inclusion initiale dans la documentation en ligne. Par conséquent, certaines procédures et rubriques peuvent être obsolètes ou incorrectes. Pour obtenir les informations les plus récentes, il est recommandé de rechercher l'objet qui vous intéresse dans l'index de la documentation en ligne.

Cette note technique décrit la mise en œuvre des constructions MFC "état de module". Une compréhension de la mise en œuvre de l’état du module est essentielle pour l’utilisation des DLL partagés MFC à partir d’un serveur en cours DLL (ou OLE).

Avant de lire cette note, consultez le site « Gérer les données d’État des modules MFC » dans [la création de nouveaux documents, fenêtres et vues.](../mfc/creating-new-documents-windows-and-views.md) Cet article contient des informations d’utilisation importantes et des informations d’aperçu sur ce sujet.

## <a name="overview"></a>Vue d’ensemble

Il existe trois types d’informations d’état MFC: l’état du module, l’état du processus et l’état de fil. Parfois, ces types d’état peuvent être combinés. Par exemple, les cartes de poignée de MFC sont à la fois module locales et thread locales. Cela permet à deux modules différents d’avoir des cartes différentes dans chacun de leurs threads.

L’état de processus et l’état de fil sont semblables. Ces éléments de données sont des choses qui ont traditionnellement été des variables globales, mais doivent être spécifiques à un processus donné ou un thread pour le soutien R gagnez32s approprié ou pour un soutien multithliant approprié. La catégorie dans laquelle s’insère un élément de données donné dépend de cet élément et de sa sémantique souhaitée en ce qui concerne les limites du processus et du thread.

L’état de module est unique en ce qu’il peut contenir l’état vraiment global ou l’état qui est le processus local ou fil local. En outre, il peut être commuté rapidement.

## <a name="module-state-switching"></a>Changement d’état de module

Chaque thread contient un pointeur sur l’état du module "actuel" ou "actif" (sans surprise, le pointeur fait partie de l’état local fil de MFC). Ce pointeur est modifié lorsque le fil d’exécution passe une limite de module, comme une application appelant à un contrôle OLE ou DLL, ou un contrôle OLE rappelant dans une application.

L’état actuel du module `AfxSetModuleState`est commuté en appelant . Pour la plupart, vous ne traiterez jamais directement avec l’API. MFC, dans de nombreux cas, l’appellera pour vous (chez `AfxWndProc`WinMain, OLE entry-points, , etc.). Ceci est fait dans n’importe quel composant `WndProc`que vous `WinMain` écrivez en reliant statiquement dans un spécial , et un spécial (ou `DllMain`) qui sait quel état de module doit être à jour. Vous pouvez voir ce code en regardant DLLMODUL. RPC ou APPMODUL. CPP dans l’annuaire MFC-SRC.

Il est rare que vous voulez définir l’état du module, puis ne pas le mettre en arrière. La plupart du temps, vous voulez "pousser" votre propre état de module comme le courant et puis, après avoir terminé, "pop" le contexte original de retour. Cela se fait [AFX_MANAGE_STATE](reference/extension-dll-macros.md#afx_manage_state) par la macro AFX_MANAGE_STATE `AFX_MAINTAIN_STATE`et la classe spéciale .

`CCmdTarget`a des caractéristiques spéciales pour soutenir la commutation de l’état du module. En particulier, `CCmdTarget` a est la classe de racine utilisée pour l’automatisation OLE et OLE COM points d’entrée. Comme tout autre point d’entrée exposé au système, ces points d’entrée doivent définir l’état du module correct. Comment un `CCmdTarget` donné sait-il ce que l’état du module "correct" devrait être La réponse est qu’il "se souvient" de ce que l’état du module "courant" est quand il est construit, de sorte qu’il peut définir l’état actuel du module à cette valeur "rappelé" quand il est appelé plus tard. Par conséquent, le module indique `CCmdTarget` qu’un objet donné est associé à l’état du module qui était à jour lorsque l’objet a été construit. Prenez un exemple simple de chargement d’un serveur INPROC, la création d’un objet, et d’appeler ses méthodes.

1. Le DLL est chargé `LoadLibrary`par OLE à l’aide de .

1. `RawDllMain`est appelé en premier. Il définit l’état du module à l’état du module statique connu pour le DLL. Pour cette `RawDllMain` raison est statiquement liée à la DLL.

1. Le constructeur de l’usine de classe associée à notre objet est appelé. `COleObjectFactory`est dérivé `CCmdTarget` et, par conséquent, il se souvient dans quel état de module il a été instantané. Ceci est important - lorsque l’usine de classe est invité à créer des objets, il sait maintenant quel état de module pour rendre à jour.

1. `DllGetClassObject`est appelé pour obtenir l’usine de classe. MFC recherche la liste d’usine de classe associée à ce module et la renvoie.

1. `COleObjectFactory::XClassFactory2::CreateInstance` est appelée. Avant de créer l’objet et de le retourner, cette fonction définit l’état du module `COleObjectFactory` à l’état du module qui était en cours dans l’étape 3 (celle qui était actuelle lorsque l’a été instantané). Cela se fait à l’intérieur de [METHOD_PROLOGUE](com-interface-entry-points.md).

1. Lorsque l’objet est créé, `CCmdTarget` il est aussi `COleObjectFactory` un dérivé et de la même manière rappelé quel état du module était actif, il en va de ce nouvel objet. Maintenant, l’objet sait à quel état de module passer chaque fois qu’il est appelé.

1. Le client appelle une fonction sur l’objet `CoCreateInstance` OLE COM qu’il a reçu de son appel. Lorsque l’objet est `METHOD_PROLOGUE` appelé il utilise `COleObjectFactory` pour changer l’état du module tout comme le fait.

Comme vous pouvez le voir, l’état du module est propagé d’objet en objet au fur et à mesure qu’ils sont créés. Il est important d’avoir l’état du module défini de manière appropriée. S’il n’est pas défini, votre objet DLL ou COM peut interagir mal avec une application MFC qui l’appelle, ou peut être incapable de trouver ses propres ressources, ou peut échouer d’autres façons misérables.

Notez que certains types de DLL, en particulier "MFC Extension" `RawDllMain` DLLs ne changent pas `RawDllMain`l’état du module dans leur (en fait, ils n’ont généralement même pas un ). C’est parce qu’ils sont destinés à se comporter "comme si" ils étaient effectivement présents dans l’application qui les utilise. Ils font partie intégrante de l’application qui est en cours d’exécution et ils ont l’intention de modifier l’état mondial de cette application.

Les contrôles OLE et autres DLL sont très différents. Ils ne veulent pas modifier l’état de la demande d’appel; l’application qui les appelle peut même ne pas être une application MFC et il peut donc y avoir aucun état à modifier. C’est la raison pour laquelle la commutation de l’état du module a été inventée.

Pour les fonctions exportées à partir d’un DLL, comme celui qui lance une boîte de dialogue dans votre DLL, vous devez ajouter le code suivant au début de la fonction:

```cpp
AFX_MANAGE_STATE(AfxGetStaticModuleState())
```

Cela échange l’état actuel du module avec l’état retourné de [AfxGetStaticModuleState](reference/extension-dll-macros.md#afxgetstaticmodulestate) jusqu’à la fin de la portée actuelle.

Des problèmes avec les ressources dans les DLLs se produiront si le AFX_MODULE_STATE macro n’est pas utilisé. Par défaut, MFC utilise le handle de ressource d'application principale pour charger le modèle de ressources. Ce modèle est réellement enregistré dans la DLL. La cause profonde est que les informations d’état du module MFC n’a pas été commutée par la macro AFX_MODULE_STATE. Le handle de ressources est récupéré de l'état du module MFC. Ne pas afficher l'état du module provoque l'utilisation du mauvais handle de ressource.

AFX_MODULE_STATE n’a pas besoin d’être mis dans toutes les fonctions dans le DLL. Par exemple, `InitInstance` peut être appelé par le code MFC dans l’application sans `InitInstance` AFX_MODULE_STATE parce que MFC déplace automatiquement l’état du module avant, puis le commutateur en arrière après `InitInstance` les retours. Il en va de même pour tous les gestionnaires de cartes de messages. Les DLFC MFC réguliers ont en fait une procédure spéciale de fenêtre principale qui change automatiquement l’état du module avant d’acheminer n’importe quel message.

## <a name="process-local-data"></a>Traiter les données locales

Traiter les données locales ne serait pas si préoccupante si elle n’avait pas été à la difficulté du modèle Win32s DLL. Dans Win32s, tous les DLL partagent leurs données globales, même lorsqu’elles sont chargées par plusieurs applications. Ceci est très différent du "vrai" modèle de données Win32 DLL, où chaque DLL obtient une copie séparée de son espace de données dans chaque processus qui se fixe à la DLL. Pour ajouter à la complexité, les données allouées sur le tas dans un Win32s DLL est en fait spécifique processus (au moins dans la mesure où la propriété va). Considérez les données et le code suivants :

```cpp
static CString strGlobal; // at file scope

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, strGlobal);
}
```

Considérez ce qui se passe si le code ci-dessus est situé dans un DLL et que DLL est chargé par deux processus A et B (il pourrait, en fait, être deux cas de la même application). Un `SetGlobalString("Hello from A")`appel . En conséquence, la mémoire est `CString` allouée pour les données dans le `CString` contexte du processus A. Gardez à l’esprit que le lui-même est global et est visible à la fois A et B. Maintenant B `GetGlobalString(sz, sizeof(sz))`appelle . B sera en mesure de voir les données que l’ensemble A. C’est parce que Win32s n’offre aucune protection entre les processus comme Win32 ne. C’est le premier problème; dans de nombreux cas, il n’est pas souhaitable que une seule application ait une incidence sur les données mondiales qui sont considérées comme appartenant à une application différente.

Il y a aussi d’autres problèmes. Disons que A sort maintenant. Lorsque A sort, la mémoire`strGlobal`utilisée par la chaîne ' est mise à disposition pour le système - c’est-à-dire, toute la mémoire allouée par le processus A est libérée automatiquement par le système d’exploitation. Il n’est `CString` pas libéré parce que le destructeur est appelé; il n’a pas encore été appelé. Il est libéré simplement parce que l’application qui l’a alloué a quitté la scène. Maintenant, si `GetGlobalString(sz, sizeof(sz))`B appelé , il peut ne pas obtenir des données valides. Une autre application peut avoir utilisé cette mémoire pour autre chose.

Il est clair qu’il existe un problème. MFC 3.x a utilisé une technique appelée stockage thread-local (TLS). MFC 3.x allouerait un indice TLS qui, sous Win32s, agit vraiment comme un indice de stockage de processus local, même s’il n’est pas appelé cela et ferait ensuite référence à toutes les données basées sur cet indice TLS. Ceci est similaire à l’indice TLS qui a été utilisé pour stocker des données thread-local sur Win32 (voir ci-dessous pour plus d’informations sur ce sujet). Cela a amené chaque MFC DLL à utiliser au moins deux indices TLS par processus. Lorsque vous comptez pour le chargement de nombreux DLL de contrôle OLE (OCX), vous êtes rapidement à court d’indices TLS (il n’y en a que 64 disponibles). En outre, MFC a dû placer toutes ces données en un seul endroit, dans une seule structure. Il n’était pas très extensible et n’était pas idéal en ce qui concerne son utilisation des indices TLS.

MFC 4.x aborde cela avec un ensemble de modèles de classe que vous pouvez «envelopper» autour des données qui devraient être processus local. Par exemple, le problème mentionné ci-dessus pourrait être résolu par écrit :

```cpp
struct CMyGlobalData : public CNoTrackObject
{
    CString strGlobal;
};
CProcessLocal<CMyGlobalData> globalData;

__declspec(dllexport)
void SetGlobalString(LPCTSTR lpsz)
{
    globalData->strGlobal = lpsz;
}

__declspec(dllexport)
void GetGlobalString(LPCTSTR lpsz, size_t cb)
{
    StringCbCopy(lpsz, cb, globalData->strGlobal);
}
```

MFC met cela en œuvre en deux étapes. Tout d’abord, il ya une couche sur le dessus de la Win32 __\* Tls__ API (**TlsAlloc**, **TlsSetValue**, **TlsGetValue**, etc) qui utilisent seulement deux index TLS par processus, peu importe combien de DLL vous avez. Deuxièmement, `CProcessLocal` le modèle est fourni pour accéder à ces données. Il remplace l’opérateur-> qui est ce qui permet la syntaxe intuitive que vous voyez ci-dessus. Tous les objets `CProcessLocal` qui sont `CNoTrackObject`enveloppés par doivent être dérivés de . `CNoTrackObject`fournit un allocateur de niveau inférieur (**LocalAlloc**/**LocalFree**) et un destructeur virtuel de sorte que MFC peut automatiquement détruire le processus des objets locaux lorsque le processus est terminé. Ces objets peuvent avoir un destructeur personnalisé si un nettoyage supplémentaire est nécessaire. L’exemple ci-dessus n’en nécessite pas, puisque le compilateur `CString` générera un destructeur par défaut pour détruire l’objet intégré.

Cette approche présente d’autres avantages intéressants. Non seulement `CProcessLocal` tous les objets sont détruits automatiquement, mais ils ne sont pas construits tant qu’ils ne sont pas nécessaires. `CProcessLocal::operator->`instantanément l’objet associé la première fois qu’il est appelé, et pas plus tôt. Dans l’exemple ci-dessus,`strGlobal`cela signifie que la « `SetGlobalString` `GetGlobalString` corde » ne sera pas construite avant la première fois ou est appelée. Dans certains cas, cela peut aider à réduire le temps de démarrage DLL.

## <a name="thread-local-data"></a>Thread Données locales

Semblable au traitement des données locales, les données locales de thread sont utilisées lorsque les données doivent être locales à un thread donné. Autrement dit, vous avez besoin d’une instance distincte des données pour chaque thread qui accède à ces données. Cela peut souvent être utilisé au lieu de vastes mécanismes de synchronisation. Si les données n’ont pas besoin d’être partagées par plusieurs threads, ces mécanismes peuvent être coûteux et inutiles. Supposons que `CString` nous avions un objet (un peu comme l’échantillon ci-dessus). Nous pouvons le faire fil local `CThreadLocal` en l’enveloppant avec un modèle:

```cpp
struct CMyThreadData : public CNoTrackObject
{
    CString strThread;
};
CThreadLocal<CMyThreadData> threadData;

void MakeRandomString()
{
    // a kind of card shuffle (not a great one)
    CString& str = threadData->strThread;
    str.Empty();
    while (str.GetLength() != 52)
    {
        unsigned int randomNumber;
        errno_t randErr;
        randErr = rand_s(&randomNumber);

        if (randErr == 0)
        {
            TCHAR ch = randomNumber % 52 + 1;
            if (str.Find(ch) <0)
            str += ch; // not found, add it
        }
    }
}
```

Si `MakeRandomString` on appelait de deux threads différents, chacun "shuffle" la chaîne de différentes manières sans interférer avec l’autre. C’est parce qu’il ya effectivement une `strThread` instance par thread au lieu d’une seule instance globale.

Notez comment une référence `CString` est utilisée pour capturer l’adresse une fois au lieu d’une fois par itération en boucle. Le code de boucle `threadData->strThread` aurait`str`pu être écrit avec partout ' ' est utilisé, mais le code serait beaucoup plus lent dans l’exécution. Il est préférable de mettre en cache une référence aux données lorsque ces références se produisent en boucles.

Le `CThreadLocal` modèle de classe `CProcessLocal` utilise les mêmes mécanismes que les mêmes mécanismes et les mêmes techniques de mise en œuvre.

## <a name="see-also"></a>Voir aussi

[Notes techniques par numéro](../mfc/technical-notes-by-number.md)<br/>
[Notes techniques par catégorie](../mfc/technical-notes-by-category.md)
