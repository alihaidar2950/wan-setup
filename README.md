# Wan 2.2 + LTX-2.5 على RunPod: فيديو AI بلا credits

**دليل خطوة بخطوة، بالعربي والإنكليزي · Step-by-step guide, Arabic and English**

From the reel by [@alihaidar.dev](https://www.instagram.com/alihaidar.dev/). Written from the setup we
ran on 2026-11-18/19. Prices change; check them on runpod.io before you start.

---

## بالعربي

### شو هو هيدا؟

بدل ما تدفع ع كل فيديو (credits)، بتستأجر كرت شاشة قوي بالساعة وبتشغّل عليه موديلات فيديو
**open weight** ببلاش:

- **Wan 2.2** من علي بابا (رخصة Apache 2.0: مسموح لأي استعمال، حتى شغل الزباين)
- **LTX-2.5** من Lightricks (ببلاش للشركات اللي مدخولها أقل من 10 مليون دولار بالسنة)

### قديش بيكلّف؟

| شو | السعر |
| --- | --- |
| كرت RTX 5090 (32 GB) على RunPod | **$1.39 بالساعة** وهو شغّال |
| تخزين (network volume) 100–200 GB للموديلات | تقريباً $7–14 بالشهر |
| فيديو 5 ثواني بـ Wan 2.2 14B | تقريباً دقيقتين → 20 فيديو وأكتر بالساعة |
| فيديو 5 ثواني بـ LTX-2.5 (مع صوت) | تقريباً 20 ثانية |

⚠️ **وقّف الـpod لما تخلّص.** الـpod بيحسب عليك ع الساعة حتى لو قاعد ما عم يعمل شي.

### بشو منيح وبشو لأ

- ممتاز: منتجات، أكل، أماكن، طبيعة، b-roll، مسودات إعلانات، خلفيات للمواقع
- أضعف: الوجوه من قريب (بتتغيّر). للقطات وجوه، بعد Kling أو Veo أحسن

### الخطوات

1. **حساب:** اعمل حساب على runpod.io وحط $10–25 رصيد.
2. **تخزين:** Storage ← New Network Volume ← 100–200 GB، بمركز بيانات فيه RTX 5090 (مثلاً EU-RO-1).
3. **Pod:** Pods ← Deploy ← RTX 5090 ← template اسمو **ComfyUI - CUDA 13.0** (الرسمي). ركّب الـvolume
   على `/workspace` وافتح port 8188. Deploy.
4. **افتح ComfyUI:** Connect ← HTTP 8188. حدّث ComfyUI لآخر نسخة (LTX-2.5 بدو ComfyUI جديد).
5. **Templates:** بـ ComfyUI: Workflow ← Browse Templates ← Video، واختار:
   - Wan 2.2 14B Text to Video (شغّل الـLightning LoRA تبع 4 steps للسرعة)
   - LTX-2.5 Text to Video
   كبوس **Download** ع الموديلات الناقصة. بينحفظوا ع الـvolume مرة وحدة.
   LTX-2.5 بدو حساب Hugging Face ببلاش: اقبل الرخصة على huggingface.co/Lightricks/LTX-2.5 أول.
6. **عامودي للريلز:** width 720 و height 1280.
7. **Prompt:** اوصف اللقطة، حركة الكاميرا والضو. مثلاً:
   *"Slow-motion coffee pouring into a ceramic cup, morning window light, steam, shallow depth of field"*.
   حط بالـqueue قد ما بدك.
8. **نزّل** الفيديوهات من الـoutput، وبعدين **Stop** للـpod (مش Terminate).

---

## English

### What this is

Instead of paying per clip, rent a strong GPU by the hour and run **open-weight** video models on it:

- **Wan 2.2** by Alibaba (Apache 2.0: any use, including client work)
- **LTX-2.5** by Lightricks (free for companies under $10M annual revenue)

### Cost (checked 2026-11-18)

| Item | Price |
| --- | --- |
| RTX 5090 (32 GB) pod, Secure Cloud | **$1.39/hour while it's on** |
| 100–200 GB network volume for the models | about $7–14/month |
| Wan 2.2 14B, 5 s clip at 720×1280 | about 2 min → 20+ clips/hour |
| LTX-2.5, 5 s clip with sound | about 20 s once loaded |

⚠️ **Stop the pod when you're done.** An idle pod bills the same as a busy one.

### Honest limits

- Great for products, food, places, nature, abstract loops, b-roll, ad drafts, website hero loops.
- Weaker on close-ups of real faces (they drift). Use Kling or Veo for those shots.

### Steps

1. **Account:** sign up at runpod.io and add $10–25 of credit.
2. **Storage:** Storage → New Network Volume → 100–200 GB, in a data centre that has RTX 5090
   (EU-RO-1 had them).
3. **Pod:** Pods → Deploy → RTX 5090 → template **"ComfyUI - CUDA 13.0"** (official). Attach the volume
   at `/workspace`, expose port 8188, Deploy.
4. **Open ComfyUI:** Connect → HTTP 8188. Update ComfyUI to the latest version (LTX-2.5 needs a recent
   ComfyUI).
5. **Templates:** Workflow → Browse Templates → Video:
   - "Wan 2.2 14B Text to Video" (turn on the 4-step Lightning LoRA for speed)
   - "LTX-2.5 Text to Video"
   Click **Download** on the missing models; they save to your volume once. LTX-2.5 needs a free
   Hugging Face account: accept the licence at huggingface.co/Lightricks/LTX-2.5 first.
6. **Vertical:** width 720, height 1280 for Reels/TikTok/Shorts.
7. **Prompt:** describe the shot, the camera move and the light, e.g. *"Slow-motion coffee pouring into a
   ceramic cup, morning window light, steam, shallow depth of field"*. Queue as many as you like.
8. **Download** the clips from the output, then **Stop** the pod (not Terminate).

### Next level

- Upscale to 1080p with SeedVR2 and smooth Wan's 16 fps with RIFE (both are ComfyUI nodes).
- Queue 50 prompts before bed and pick the best in the morning.

### Links

- Wan 2.2: https://huggingface.co/Wan-AI/Wan2.2-T2V-A14B
- LTX-2.5: https://huggingface.co/Lightricks/LTX-2.5
- RunPod pricing: https://www.runpod.io/pricing

---

### What next? · شو بعد؟

- ⭐ Star this repo if it helped, so more people find it.
- Follow [@alihaidar.dev](https://www.instagram.com/alihaidar.dev/) on Instagram or [TikTok](https://www.tiktok.com/@alihaidar.dev) for the next free guide.
- All my free guides: [github.com/alihaidar2950](https://github.com/alihaidar2950?tab=repositories)

<div dir="rtl">

إذا فادك، حطّ ⭐ عالـrepo، وتابعني عَ [إنستغرام](https://www.instagram.com/alihaidar.dev/) أو [تيك توك](https://www.tiktok.com/@alihaidar.dev) لتوصلك الأداة الجاية ببلاش.

</div>
