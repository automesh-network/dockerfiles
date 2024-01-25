FROM chocolatey

RUN choco install rustup.install -y
RUN choco install visualstudio2022buildtools -y --package-parameters '--quiet --wait --norestart --add Microsoft.Component.MSBuild --add Microsoft.VisualStudio.Component.Windows11SDK.22621 --add Microsoft.VisualStudio.Component.VC.Tools.x86.x64'
