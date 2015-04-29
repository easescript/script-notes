To disable repacking of jars:

    %define __jar_repack %{nil}

or

    %define _\_os\_install_post %{nil}

To find out %{__spec_install_post}:

    # rpm --eval %__spec_install_post
