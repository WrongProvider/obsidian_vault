
# 1) Persist the override
echo 'export PLAYWRIGHT_HOST_PLATFORM_OVERRIDE=ubuntu24.04-x64' >> ~/.bashrc
source ~/.bashrc

# 2) Install browsers (works for chromium, firefox, webkit)
npx playwright install chromium

# 3) Install runtime libs — Ubuntu 26 ships t64 lib variants (y2038 transition)
sudo apt update
sudo apt install -y \
  libnss3 libnspr4 \
  libatk1.0-0t64 libatk-bridge2.0-0t64 libatspi2.0-0t64 \
  libcups2t64 \
  libxkbcommon0 libxcomposite1 libxdamage1 libxfixes3 libxrandr2 \
  libgbm1 libdrm2 \
  libpango-1.0-0 libcairo2 \
  libasound2t64 libwayland-client0