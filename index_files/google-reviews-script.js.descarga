if (window.mkpGoogleScriptValidation != "running") {
  console.log("Running Google Reviews Script Updated");

  window.mkpGoogleScriptValidation = "running";

  window.runScriptGoogleReviews = function () {
    //*** Global Variables - Start */
    // main endpoints
    const cdnBaseUrl =
      "https://mkp-prod.nyc3.cdn.digitaloceanspaces.com/google-reviews";
    const backendUrl = "https://us-east1-goog-reviews-wix.cloudfunctions.net";
    const appId = "f20b0377-bc3e-418d-9d73-2ac147543483";
    const instanceId = document
      .getElementById("mkp_gg_reviews_script")
      .src.split("instance_id=")[1];
    const vueScriptUrl = cdnBaseUrl + "/vue_widget/app.js"; // should placed in 'vue_widget/' directory

    const MKPGlobalVars = {
      cdnUrl: cdnBaseUrl,
      appId: appId,
      backendUrl: backendUrl,
      instanceId: instanceId,
    };

    var MKPAfHttpClient = function () {
      this.get = function (aUrl, aCallback) {
        var anHttpRequest = new XMLHttpRequest();
        anHttpRequest.onreadystatechange = function () {
          if (anHttpRequest.readyState == 4 && anHttpRequest.status == 200)
            aCallback(anHttpRequest.responseText);
        };
        anHttpRequest.open("GET", aUrl, true);
        anHttpRequest.send(null);
      };
    };

    // Reviews data
    let filteredReviews = [];
    let reviewsStatistics = {
      reviews_count: 0,
      star_count: 0,
      overall_rating: "0.0",
    };
    let filterOptions = {
      review_filter: "all",
      widget_flow: "only-badge",
      open_behavior: "click",
    };

    let widgetData = [
      {
        xxs: [
          {
            widgetName: "review-widget_teaser",
            displayName: "Widget container",
            styles: {
              L_Bg_Padding: {
                top: 0,
                left: 0,
                bottom: 0,
                right: 0,
              },
              D_Bg_PrimaryColor: "rgba(255, 255, 255, 0)",
              L_Btn_Direction: "horizontal",
              L_MinHeight: 40,
              ani_ShowAfter: 1.5,
              position_Left: 12,
              D_Bg_SecondaryColor: "rgba(46, 129, 255, 1)",
              position_Right: "unset",
              L_Bg_MobilePadding: {
                top: 0,
                left: 0,
                bottom: 0,
                right: 0,
              },
              L_ElementGap: 0,
              L_MaxHeight: 300,
              position_Bottom: 12,
              ani_Type: "fade",
              D_Bg_Blur: 0,
              position_Top: "unset",
              D_Bg_BdrWidth: 0,
              L_Bg_CRadius: 6,
              D_Bg_BdrColor: "rgb(255, 255, 255)",
              position: "left-bottom",
              D_Bg_Enable_Gradient: false,
              L_MaxWidth: 320,
              L_Bdg_MobileLayout: "default-badge",
              mobilePosition: "center-bottom",
              L_Btn_MobileDirection: "horizontal",
              mobilePosition_Left: 0,
              mobilePosition_Right: 0,
              mobilePosition_Top: "unset",
              mobilePosition_Bottom: 12,
            },
            id: "container",
            type: "widget",
          },
          {
            iconName: "builder/icon-element-image",
            displayName: "Review badge",
            moved: false,
            h: 6,
            description: "HTML <img> tag",
            i: "1",
            label: "Review badge",
            type: "review_badge",
            bdg_text_afterReviewCount: "REVIEWS",
            w: 4,
            x: 0,
            y: 0,
            styles: {
              D_Bdg_Enable_Gradient: false,
              D_Label_TextColor: "#f7802f",
              D_Bdg_SecondaryColor: "rgb(255, 255, 255)",
              L_Bdg_Template: "bdg_3",
              D_Bdg_BdrColor: "#e5e5e5",
              D_Bdg_IconFB_Color: "#1976d2",
              D_TextColor: "rgba(0, 0, 0, 1)",
              D_Label_FontSize: 18,
              L_Bdg_IconStr_Gap: 0,
              D_Label_Font_Formats: [],
              D_Label_TextFont: "Poppins",
              D_Bdg_IconStrOff_Color: "#d9d9d9",
              D_Bdg_Logo: "original_logo",
              D_FontSize: 12,
              L_Bdg_IconStr_Size: 25,
              L_Bdg_ElementGap: 0,
              D_BdgStars_Color: "rgba(255, 56, 92,1)",
              L_Bdg_IconFB_Size: 42,
              D_Bdg_BdrWidth: 1,
              D_ColorScheme: "color_1",
              D_Bdg_IconStrOn_Color: "#f7802f",
              D_Font_Formats: [],
              D_Bdg_PrimaryColor: "rgb(255, 255, 255)",
              L_Bdg_Radius: 6,
              L_Bdg_Padding: {
                top: 6,
                left: 12,
                bottom: 6,
                right: 12,
              },
              D_TextFont: "Poppins",
              L_Bdg_Icon_Size: 42,
            },
            id: "review_badge_0",
            reviews_overall: {
              overall_rating: "5",
              star_count: "158",
              reviews_count: "100",
            },
          },
        ],
        lg: [
          {
            widgetName: "review-widget_teaser",
            displayName: "Widget container",
            styles: {
              L_Bg_Padding: {
                top: 0,
                left: 0,
                bottom: 0,
                right: 0,
              },
              D_Bg_PrimaryColor: "rgba(255, 255, 255, 0)",
              L_Btn_Direction: "horizontal",
              L_MinHeight: 40,
              ani_ShowAfter: 1.5,
              position_Left: 12,
              D_Bg_SecondaryColor: "rgba(46, 129, 255, 1)",
              position_Right: "unset",
              L_Bg_MobilePadding: {
                top: 0,
                left: 0,
                bottom: 0,
                right: 0,
              },
              L_ElementGap: 0,
              L_MaxHeight: 300,
              position_Bottom: 12,
              ani_Type: "fade",
              D_Bg_Blur: 0,
              position_Top: "unset",
              D_Bg_BdrWidth: 0,
              L_Bg_CRadius: 6,
              D_Bg_BdrColor: "rgb(255, 255, 255)",
              position: "left-bottom",
              D_Bg_Enable_Gradient: false,
              L_MaxWidth: 320,
              L_Bdg_MobileLayout: "default-badge",
              mobilePosition: "center-bottom",
              L_Btn_MobileDirection: "horizontal",
              mobilePosition_Left: 0,
              mobilePosition_Right: 0,
              mobilePosition_Top: "unset",
              mobilePosition_Bottom: 12,
            },
            id: "container",
            type: "widget",
          },
          {
            iconName: "builder/icon-element-image",
            displayName: "Review badge",
            moved: false,
            h: 6,
            description: "HTML <img> tag",
            i: "1",
            label: "Review badge",
            type: "review_badge",
            bdg_text_afterReviewCount: "REVIEWS",
            w: 4,
            x: 0,
            y: 0,
            styles: {
              D_Bdg_Enable_Gradient: false,
              D_Label_TextColor: "#f7802f",
              D_Bdg_SecondaryColor: "rgb(255, 255, 255)",
              L_Bdg_Template: "bdg_3",
              D_Bdg_BdrColor: "#e5e5e5",
              D_Bdg_IconFB_Color: "#1976d2",
              D_TextColor: "rgba(0, 0, 0, 1)",
              D_Label_FontSize: 18,
              L_Bdg_IconStr_Gap: 0,
              D_Label_Font_Formats: [],
              D_Label_TextFont: "Poppins",
              D_Bdg_IconStrOff_Color: "#d9d9d9",
              D_Bdg_Logo: "original_logo",
              D_FontSize: 12,
              L_Bdg_IconStr_Size: 25,
              L_Bdg_ElementGap: 0,
              D_BdgStars_Color: "rgba(255, 56, 92,1)",
              L_Bdg_IconFB_Size: 42,
              D_Bdg_BdrWidth: 1,
              D_ColorScheme: "color_1",
              D_Bdg_IconStrOn_Color: "#f7802f",
              D_Font_Formats: [],
              D_Bdg_PrimaryColor: "rgb(255, 255, 255)",
              L_Bdg_Radius: 6,
              L_Bdg_Padding: {
                top: 6,
                left: 12,
                bottom: 6,
                right: 12,
              },
              D_TextFont: "Poppins",
              L_Bdg_Icon_Size: 42,
            },
            id: "review_badge_0",
            reviews_overall: {
              overall_rating: "5",
              star_count: "158",
              reviews_count: "100",
            },
          },
        ],
      },
    ];

    let widgetVisibility = {
      visibility_status: true,
      visibility_option: "home-only",
    };
    let subscriptionPlan = "Free";
    let connectedPage = {
      id: "",
      name: "",
      listingName: "",
      profilePictureURL: "",
    };

    // Permission keys
    let isPreviewMode = false;
    /** flag use for hide widget in dashboard app web previews */
    let isWidgetDataAvailable = true;
    let isHomePage = true;

    //*** Global Variables - End */

    // Run functions
    bindGlobalVariables();
    bindVueWidget();
    mkpFetchReviewsData();
    // checkAndAddWidgets();

    //*** Functions - Start */
    function bindGlobalVariables() {
      //Add main/global variables into head
      const MKPGlobalVarsScript = document.createElement("script");
      MKPGlobalVarsScript.setAttribute(
        "MkpGoogleReviewsGlobalVars",
        JSON.stringify(MKPGlobalVars)
      );
      MKPGlobalVarsScript.id = "MKP-GOOGLE-REVIEWS-GLOBAL-VARS";
      document.head.appendChild(MKPGlobalVarsScript);
    }

    function bindVueWidget() {
      //Add vue widget .js and .css file into the head
      const MKPImportedVueComps = document.createElement("script");
      MKPImportedVueComps.src = vueScriptUrl;
      document.head.appendChild(MKPImportedVueComps);
    }

    function mkpRegisterListener() {
      window.wixDevelopersAnalytics.register(
        MKPGlobalVars.appId,
        (eventName, eventParams) => {
          switch (eventName) {
            case "PageView":
              const pagePath = eventParams.pagePath;
              isHomePage = pagePath === "/";
              checkAndAddWidgets();
              break;
            case "ViewContent":
              //isHomePage = pagePath === "/";
              //checkAndAddWidgets();
              break;
          }
        }
      );
    }

    function mkpFetchReviewsData() {
      const backendUrl = MKPGlobalVars.backendUrl;
      const instance_id = `instance_id=${MKPGlobalVars.instanceId}`;

      const getReviewsDataUrl = `${backendUrl}/getMemberReviewsData?${instance_id}`;
      const mkpGetClient = new MKPAfHttpClient();

      mkpGetClient.get(getReviewsDataUrl, function (res) {
        const reviewsData = JSON.parse(res);
        filteredReviews = reviewsData.filtered_reviews || filteredReviews;
        reviewsStatistics = reviewsData.reviews_statistics || reviewsStatistics;
        filterOptions = reviewsData.filter_options || filterOptions;
        widgetVisibility = reviewsData.widget_visibility || widgetVisibility;
        subscriptionPlan = reviewsData.subscription_plan || subscriptionPlan;
        connectedPage = reviewsData.fb_page || connectedPage;
        const fb_widgetData = reviewsData.widget_data;

        isWidgetDataAvailable = Object.keys(widgetData).length > 0;
        if (isWidgetDataAvailable) widgetData = fb_widgetData;
        //console.log("Ⓜ️ ~ reviewsData:", reviewsData);
        //console.log("Ⓜ️ ~ widgetData:", widgetData);

        checkAndAddWidgets();
      });
    }

    function checkAndAddWidgets() {
      mkpRemoveWidget();
      const isWidgetActive = widgetVisibility.visibility_status == true;
      const visibleOnlyInHomePage =
        widgetVisibility.visibility_option === "home-only";

      if (!isWidgetActive || !isWidgetDataAvailable || isPreviewMode) {
        return;
      }
      if (visibleOnlyInHomePage && isHomePage) {
        mkpShowReviewsWidget();
      }
      if (!visibleOnlyInHomePage) {
        mkpShowReviewsWidget();
      }
      if (visibleOnlyInHomePage && !isHomePage) {
        mkpRemoveWidget();
      }
    }

    function mkpShowReviewsWidget() {
      let reviewsWidget = document.createElement("mkp-google-reviews");

      reviewsWidget.setAttribute("reviewdata", JSON.stringify(filteredReviews));
      reviewsWidget.setAttribute(
        "reviewsstatistics",
        JSON.stringify(reviewsStatistics)
      );
      reviewsWidget.setAttribute(
        "filterreviews",
        JSON.stringify(filterOptions)
      );
      reviewsWidget.setAttribute(
        "connectedpage",
        JSON.stringify(connectedPage)
      );

      const mainModalStyleData = JSON.stringify(widgetData[0]);
      const teaserStyleData = JSON.stringify(widgetData[1]);
      reviewsWidget.setAttribute("mainstyledata", mainModalStyleData);
      reviewsWidget.setAttribute("teaserstyledata", teaserStyleData);

      document.body.appendChild(reviewsWidget);
    }

    function mkpRemoveWidget() {
      let reviewsWidget = document.querySelector("mkp-google-reviews");
      if (reviewsWidget) reviewsWidget.remove();
    }

    function previewScreenCheckEvent(event) {
      // remove widget in preview mode
      if (event.data.action === "mkpHideWidget") {
        // console.log("Ⓜ️ This is preview screen: ", event.data);
        isPreviewMode = true;
        mkpRemoveWidget();
      }
    }

    //*** Functions - End */

    // check is widget page in the preview mode
    window.addEventListener("message", previewScreenCheckEvent);

    // Remove the event listener after 15 seconds
    setTimeout(() => {
      window.removeEventListener("message", previewScreenCheckEvent);
    }, 16000);

    window.wixDevelopersAnalytics
      ? mkpRegisterListener()
      : window.addEventListener(
          "wixDevelopersAnalyticsReady",
          mkpRegisterListener
        );
  };

  window.runScriptGoogleReviews();
}
