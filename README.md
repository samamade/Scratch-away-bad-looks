{
  "manifest_version": 3,
  "name": "Blur YouTube Video",
  "version": "2.0",
  "description": "إضافة لتخبيش فيديوهات اليوتيوب تلقائيا مع خيارات التحكم.",
  "permissions": ["scripting", "storage", "activeTab"],
  "host_permissions": ["https://www.youtube.com/*"],
  "action": {
    "default_popup": "popup.html",
    "default_icon": {
      "16": "icon.png",
      "48": "icon.png",
      "128": "icon.png"
    }
  },
  "background": {
    "service_worker": "background.js"
  },
  "content_scripts": [
    {
      "matches": ["https://www.youtube.com/*"],
      "js": ["content.js"]
    }
  ]
}
// استرجاع الإعدادات من التخزين
chrome.storage.sync.get(["blurLevel", "isBlurred"], (data) => {
    let blurLevel = data.blurLevel || 10; // قيمة التخبيش الافتراضية
    let isBlurred = data.isBlurred !== false; // تلقائيًا مفعّل


